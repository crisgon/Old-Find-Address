<template>
    <div>
      <div class="box" :class="{ show: showAddress }">
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
    margin: 0 auto;
    border-radius: 6px;
    background-color: #fff;
    max-height: 0;
    padding: 0;
    overflow: hidden;
    transition: 445ms cubic-bezier(0.500, 0.885, 0.32, 2.275) all;
  }

  .show{
    max-height: 999px;
    padding: .5em;
    overflow: visible;
  }

  .list-item {
    display: inline-block;
    margin-right: 10px;
  }
  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to /* .list-leave-active em versões anteriores a 2.1.8 */ {
    opacity: 0;
    transform: translateY(30px);
  }
</style>
