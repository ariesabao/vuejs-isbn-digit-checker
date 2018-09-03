<template>
  <div id="app">
    <Isbn></Isbn>
  </div>
</template>

<script>
import Isbn from './components/Isbn'

export default {
  name: 'App',
  components: {
    Isbn
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
