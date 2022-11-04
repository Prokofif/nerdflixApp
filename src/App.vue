<template>
  <div id="app">
    <!-- import font-awesome library -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
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
@font-face {
  font-family: "Source Sans Pro";
  src: url(./fonts/SourceSansPro-Regular.ttf) format("truetype");
}
@font-face {
  font-family: "Source Sans Pro Bold";
  src: url(./fonts/SourceSansPro-Bold.ttf) format("truetype");
}

#app {
  font-family: 'Source Sans Pro', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
