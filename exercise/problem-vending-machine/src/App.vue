<template>
  <div id="app">
    <h1> Vending Machine</h1>
    <HelloWorld  msg="Welcome to Your Vue.js App" :drinkingList="drinkingList" :coinList="coinList"/>
  </div>
</template>

<script>
  import HelloWorld from './components/HelloWorld.vue'
  import Products from '../../../data/products.json'

  export default {
    name: 'app',
    components: {
      HelloWorld
    },
    data() {
      return {
        drinkingList: Products,
        coinList:[10,5,2,1] 
      }
    },

  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 30px;
  }
</style>