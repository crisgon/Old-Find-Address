<template>
  <form class="form">
    <label for="cep" class="form-label">CEP:</label>
    <input type="text" class="form-input" placeholder="CEP" id="cep"
           :class="cepIsValid"
           @input="getAddress($event.target.value)">
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
        address: {}
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
        if(this.validation(cep) == 'sucess'){
          this.$http.get(`http://apps.widenet.com.br/busca-cep/api/cep/${cep}.json`)
              .then(response => response.json())
              .then(data => this.address = data, err => console.log(err));
          this.cepIsValid = 'default';
        }
      },
      sendAddress() {
        EventBus.$emit('sendData', this.address);
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
