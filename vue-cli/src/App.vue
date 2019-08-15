<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" v-if="false">
    <HelloWorld msg="Welcome to Your Vue.js App1" v-if="false"></HelloWorld>
    <test msg="123456789"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import test from './components/test.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    test
  },
  created(){
    console.log(this)
  },
  mounted() {
    console.log()
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
  margin-top: 60px;
}
</style>
