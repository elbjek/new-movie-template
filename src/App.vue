<template>
  <div id="app">

    <movie />
  </div>
</template>

<script>
import movie from './components/movie.vue'

export default {
  name: 'app',
  components: {
    movie
  }
  
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: rgb(186, 219, 218);
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
