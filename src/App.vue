<template>
  <div id="app">
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
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
</style>
