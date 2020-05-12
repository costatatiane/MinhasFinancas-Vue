<template>
  <div id="app">
    <finances></finances>
  </div>
</template>

<script>
import Finances from './components/Finances.vue'

export default {
  name: 'App',
  components: {
    finances: Finances,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
