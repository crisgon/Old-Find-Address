<template>
  <form class="form">
    <label for="cep" class="form-label">CEP:</label>
    <input type="text" class="form-input" placeholder="CEP" id="cep"
           :class="cepIsValid"
           v-model="cep"
           @input="getAddress">
    <input type="submit" class="form-btn" value="Find"
           @click.stop.prevent="sendAddress()">
  </form>
</template>

<script>
  import {EventBus} from '../../main';
  export default{
    data() {
      return {
        cepIsValid: '',
        cep: '',
      }
    },
    methods: {
      validation(e){
        let cepFormat = new RegExp('^[\\d]{3}[.]*[\\d]{2}[-]*[\\d]{3}$');
        return cepFormat.test(e)
        ? this.cepIsValid = 'sucess'
        : this.cepIsValid = 'error';
      },
      getAddress(cep) {
        this.cep = this.cep.split('').splice(0,8).join('')
        if(this.validation(cep.target.value) == 'sucess'){
          this.cepIsValid = 'default';
        } else {
          this.cepIsValid = '';
        }
      },
      sendAddress() {
        this.$http.get(`http://apps.widenet.com.br/busca-cep/api/cep/${this.cep}.json`)
              .then(response => response.json())
              .then(data => {
                EventBus.$emit('sendData', data);
                }, err => console.log(err));

      }
    }
  }
</script>

<style scoped>
  .form {
    width: 300px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    transition: 225ms cubic-bezier(0.175, 0.885, 0.32, 1.275) all
  }

  .form-label {
    width: 100%;
    font-weight: bold;
    padding: .3em 0;
  }

  .form-input {
    width: 80%;
    box-sizing: border-box;
    padding: 1em;
    margin: .5em 0;
    border-radius: 6px 0 0 6px;
    outline: 0;
    border: 0;
  }

  .form-btn {
    width: 20%;
    padding: 1em 0;
    border: 0;
    border-radius: 0 6px 6px 0;
    cursor: pointer;
  }

  .default {
    border: 0;
  }

  .error {
    border: 2px solid red;
  }

  .sucess {
    border: 2px solid blue;
  }
</style>
