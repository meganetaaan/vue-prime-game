<template>
  <div id="app">
    <Prime/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Prime from './components/Prime/Prime.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Prime
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
