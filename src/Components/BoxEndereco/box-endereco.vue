<template>
  <div class="box" v-show="showAddress">
    <h2 class="box-text">Bairro</h2>
    <span>{{ bairro }}</span>
    <h2 class="box-text">Rua</h2>
    <span>{{ rua }}</span>
    <h2 class="box-text">Cidade</h2>
    <span>{{ cidade }}</span>
    <h2 class="box-text">Estado</h2>
    <span>{{ estado }}</span>
  </div>
</template>

<script>
  export default {
    props: ['rua', 'cidade', 'bairro', 'estado', 'showAddress'],
    data() {
      return {
      }
    }
  }
</script>

<style scoped>
  .box {
    width: 300px;
    box-sizing: border-box;
    padding: .5em;
    margin: 0 auto;
    border-radius: 6px;
    background-color: #fff;
  }
</style>
