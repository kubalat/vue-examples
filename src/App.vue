<template>
  <div id="app">
    <h1>Calculate travels charge</h1>
    <Travels />
  </div>
</template>

<script>
import Travels from './components/Travels.vue'

export default {
  name: 'app',
  components: {
    Travels
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

* {
  box-sizing: border-box;
}
</style>
