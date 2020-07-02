<template>
  <div id="app">
    <History msg="adventure book"/>
  </div>
</template>

<script>
import History from './components/History.vue'

export default {
  name: 'App',
  components: {
    History
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
