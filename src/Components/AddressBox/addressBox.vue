<template>
 <div>
  <div class="box" v-show="showAddress">
    <h2 class="box-text">District</h2>
    <span>{{ this.dadosEndereco.district }}</span>
    <h2 class="box-text">Address</h2>
    <span>{{ this.dadosEndereco.address }}</span>
    <h2 class="box-text">City</h2>
    <span>{{ this.dadosEndereco.city }}</span>
    <h2 class="box-text">State</h2>
    <span>{{ this.dadosEndereco.state }}</span>
  </div>
  <span v-show="!showAddress">No address found...</span>
 </div>
</template>

<script>
  import {EventBus} from '../../main';
  export default {
    data() {
      return {
        dadosEndereco: {},
        showAddress: false
      }
    },
    created () {
      EventBus.$on('sendData', (data) => {
        this.dadosEndereco = data;
        if(this.dadosEndereco.status != 0){
          this.showAddress = true;
        }else {
          this.showAddress = false;
        }
      });
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
