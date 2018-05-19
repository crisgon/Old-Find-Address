<template>
  <div id="app">
    <formulario/>
    <endereco/>
  </div>
</template>

<script>
import Formulario from './Components/Formulario/formulario';
import BoxEndereco from './Components/BoxEndereco/box-endereco';
export default {
  name: 'app',
  components: {
    formulario: Formulario,
    endereco: BoxEndereco
  },

  data () {
    return {

    }
  }
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
