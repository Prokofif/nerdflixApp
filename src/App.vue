<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <NerdflixMovies/>
  </div>
</template>

<script> 
import NerdflixMovies from './components/NerdflixMovies.vue'

export default {
  name: 'App',
  components: {
    NerdflixMovies
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
