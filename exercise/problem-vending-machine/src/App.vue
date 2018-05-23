<template>
  <div id="app">
    <h1> Vending Machine</h1>
    <HelloWorld msg="Welcome to Your Vue.js App" :drinkingList="drinkingList" :coinList="coinList" :bankList="bankList"/>
  </div>
</template>

<script>
  import HelloWorld from './components/HelloWorld.vue'

  export default {
    name: 'app',
    components: {
      HelloWorld
    },
    data() {
      return {
        drinkingList: {},
        coinList: [10, 5, 2, 1],
        bankList:[100,50,20]
      }
    },
    beforeMount() {
      this.axios.get('http://www.mocky.io/v2/5af11f8c3100004d0096c7ed').then((response) => {
        console.log(response.data)
        this.drinkingList = response.data;
      })
    }

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