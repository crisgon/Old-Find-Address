<template>
  <div id="app">
  <h1>Find You Address</h1>
    <cepForm/>
    <addressBox/>
  </div>
</template>

<script>
import Form from './Components/Form/form';
import AddressBox from './Components/AddressBox/addressBox';
export default {
  name: 'app',
  components: {
    cepForm: Form,
    addressBox: AddressBox
  },

  data () {
    return {
    }
  },
}
</script>

<style>
  body {
    background-color: #2ed573;
  }

  #app {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    display: flex;
    flex-direction: column;
  }
</style>
