<template>
  <form class="formulario">
    <label for="cep" class="formulario-label">CEP:</label>
    <input type="text" class="formulario-input" placeholder="CEP" id="cep">
  </form>
</template>

<script>
  export default{
  }
</script>

<style scoped>
  .formulario {
    width: 300px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
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
    border: 0;
    outline: 0;
  }
</style>
