<template>
  <div class="nerdflix">
    <div class="header">
      <h1>Nerdflix</h1>
      <h2>Movies</h2>
    </div>
    <div class="movie_container">
      <div class="movie_card" v-for="(movie, index) in movies" :key="index">
        <b-card>
          <div class="rating-container">
            <img :src="movies[index].urlPoster" class="movie-image" />
            <div class="overlay">
              <div class="rating">{{ movies[index].rating }}</div>
            </div>
          </div>

          <b-card-text>
            {{ movies[index].title }}
            <p>
              {{ movies[index].year }}
            </p>
          </b-card-text>
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
  methods: {},
};
</script>

<style>
h1 {
  color: #e50914;
  text-align: center;
  background: #131313;
  text-transform: uppercase;
}
h2 {
  text-align: left;
  color: white;
  background: #171717;
  padding: 1rem;
}

h1,
h2 {
  margin-bottom: 0 !important;
  padding: 1rem;
}
.movie_container {
  background: #1d1d1d;
}

.movie_card {
  display: flex;

  display: inline-block;
  margin: 1rem;
}
img {
  border-radius: 6px;
}
.card {
  --bs-card-border-color: #1d1d1d !important;
}
div.card-body {
  min-width: 182px;
  min-height: 200px;
  background: #1d1d1d;
  color: white;
}

p.card-text {
  max-width: 182px;
  padding: 1.5rem 0.5rem;
}
p.card-text > p {
  margin: 0;
  opacity: 49.88%;
}


/* raiting styles */
.rating-container {
  position: relative; 
}

.movie-image {
  display: block; 
  height: auto;
}

.overlay {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100%;
  width: 100%;
  opacity: 0;
  transition: 0.5s ease;
  backdrop-filter: blur(2.46496px); /* Note: backdrop-filter has minimal browser support */
  border-radius: 6px;
}

.rating-container:hover .overlay {
  opacity: 1;
  width: 100%;
}

.rating {
  color: white;
  font-size: 2rem;
  position: absolute;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  text-align: center;
}
</style>
