<template>
  <div id="app">
    <formulario/>
  </div>
</template>

<script>
import Formulario from './Components/Formulario/formulario';
export default {
  name: 'app',
  components: {
    formulario: Formulario
  },

  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>
  body {
    background-color: #2ed573;
  }
</style>
