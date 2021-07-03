<template>
  <div id="app">
    
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to My Vue.js App"/>
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Calculator
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  min-width: 600px;
}
</style>


