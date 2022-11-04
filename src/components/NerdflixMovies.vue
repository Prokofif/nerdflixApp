<template>
  <div class="nerdflix">
    <div class="header">
      <h1>Nerdflix</h1>
      <h2>Movies</h2>
      <div class="sortMovies">
        <p>Sort by</p>
        <button @click="sortRating" class="sortRating">Rating</button>
        <button @click="sortAlphabet" class="sortTitle">A-Z</button>
      </div>
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
    </div>
  </div>
</template>

<script>
import json from "../json/imdb-top-50.json";

export default {
  data() {
    return {
      movies: json.data.movies,
      ascAplabet: true,
      ascRating: true,
    };
  },
  methods: {
    sortAlphabet() {
      if (this.ascAplabet) {
        this.movies = this.movies.sort((a, b) => {
          if (a.title < b.title) {
            return -1;
          }
        });
        this.ascAplabet = false;
      } else {
         this.movies = this.movies.sort((a, b) => {
          if (a.title > b.title) {
            return -1;
          }
        });
        this.ascAplabet = true;
      }

    },

    sortRating() {
      if (this.ascRating){
        this.movies = this.movies.sort((a, b) => {
          if (a.rating > b.rating) {
            return -1;
          }
        });
        this.ascRating = false;
      } else {
        this.movies = this.movies.sort((a, b) => {
          if (a.rating < b.rating) {
            return -1;
          }
        });
        
        this.ascRating = true;
      }
    },
  },
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
  min-width: 213.97px;
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

.rating-container {
  position: relative;
}

.movie-image {
  display: block;
  height: auto;
}

/* raiting style */
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
  backdrop-filter: blur(
    2.46496px
  ); /* Note: backdrop-filter has minimal browser support */
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

.sortMovies {
  color: white;
}
.sortMovies > p {
  background: #131313;
  margin: 0;
  padding: 0;
  color: white;

  position: absolute;
  opacity: 0.5;
  left: 70.07%;
  right: 19.44%;
  top: 8.65%;
  bottom: 85.13%;
}

.sortTitle,
.sortRating {
  color: white;
  box-sizing: border-box;
  position: absolute;
  background: #131313;
  border: 1px solid #2e2e2e;
  border-radius: 6px;
}

.sortTitle {
  left: 70.07%;
  right: 19.44%;
  top: 11.65%;
  bottom: 85.13%;
}
.sortRating {
  left: 82.64%;
  right: 6.88%;
  top: 11.65%;
  bottom: 85.13%;
}
</style>
