<template>
  <form class="formulario">
    <label for="cep" class="formulario-label">CEP:</label>
    <input type="text" :class="cepValido" class="formulario-input" placeholder="CEP" id="cep" @input="validacao($event.target.value)">
  </form>
</template>

<script>
  export default{
    data() {
      return {
        cepValido: ''
      }
    },
    methods: {
      validacao(e){
        let cepFormat =new RegExp('^[\\d]{3}[.]*[\\d]{2}[-]*[\\d]{3}$');
        cepFormat.test(e)
        ? this.cepValido = 'acerto'
        : this.cepValido = 'erro';
      }
    }
  }
</script>

<style scoped>
  .formulario {
    width: 300px;
  }

  .formulario-label {
    font-weight: bold;
    padding: .3em 0;
  }

  .formulario-input {
    width: 100%;
    box-sizing: border-box;
    padding: 1em;
    margin: .5em 0;
    border-radius: 6px;
    outline: 0;
  }

  .padrao {
    border: 0;
  }

  .erro {
    border: 2px solid red;
  }

  .acerto {
    border: 2px solid blue;
  }
</style>
