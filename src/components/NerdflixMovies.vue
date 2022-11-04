<template>
  <div class="nerdflix">
    <div class="header">
      <h1>Nerdflix</h1>
      <h2>Movies</h2>
    </div>
    <div class="movie_container">
      <div class="movie_cards" v-for="(movie, index) in movies" :key="index">
        <b-card>
          {{ movies[index].title }}
          {{ movies[index].rating }}
          <img :src="movies[index].urlPoster" />
        </b-card>
      </div>
      <button @click="mov">ok</button>
    </div>
  </div>
</template>

<script>
import json from "../json/imdb-top-50.json";

export default {
  data() {
    return {
      movies: json.data.movies,
    };
  },
  methods: {
    mov() {
      console.log("hello");
      let n = JSON.stringify(this.movies.data.movies[0].title);
      console.log(n);
      // let element;
      // for (let index = 0; index < this.movies.length; index++) {

      // console.log(element);
      // }
    },
  },
};
</script>

<style>
h1 {
  color: #e50914;
  text-align: center;
  background: #131313;
}
h2 {
  text-align: left;
  color: white;
  background: #171717;
}

h1,
h2 {
  margin-bottom: 0 !important;
  padding: 0.5rem 0;
}
.movie_cards {
  display: flex;
  flex-wrap: wrap;
  background: #1d1d1d;
}
</style>