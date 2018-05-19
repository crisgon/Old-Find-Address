<template>
  <div class="box" v-show="hasAddress">
    <h2 class="box-text">Bairro</h2>
    <span>Barreiro</span>
    <h2 class="box-text">Rua</h2>
    <span>Barreiro</span>
    <h2 class="box-text">Cidade</h2>
    <span>Barreiro</span>
    <h2 class="box-text">Estado</h2>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        hasAddress: false
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
