<template>
  <div id="app">
    <Top></Top>
  </div>
</template>

<script>
import Top from './views/Top.vue'

export default {
  name: 'App',
  components: {
    Top
  }
}
</script>

<style>
*{
    margin: 0;
    padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
