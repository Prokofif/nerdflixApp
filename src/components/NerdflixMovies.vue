<template>
  <div class="nerdflix">
    <div class="header">
      <!-- <button>Homepage</button>
      <button>Series</button>
      <button>Movies</button> -->
      <h1>Nerdflix</h1>
      <h2 class="movies-header">Movies</h2>
      <div class="star-header">
        <i class="fa fa-star-o" style="font-size: 1.8rem; color: #f8e71c"></i
        ><span class="favorit-movies">{{ this.favoritMovies }} </span>
      </div>
      <div class="sort-movies">
        <p>Sort by</p>
        <button @click="sortRating" class="sort-rating">Rating</button>
        <button @click="sortAlphabet" class="sort-title">Title A-Z</button>
      </div>
    </div>
    <div class="movie-container">
      <div class="movie-card" v-for="(movie, index) in movies" :key="index">
        <b-card>
          <div class="rating-container">
            <img :src="movies[index].urlPoster" class="movie-image" />
            <div class="rating-overlay">
              <div class="rating">{{ movies[index].rating }}</div>
              <div v-if="movies[index].favorit">
                <i
                  class="fa fa-star-o star-favorite"
                  style="font-size: 1.8rem; color: #f8e71c"
                  @click="addFavoritMovie(index, movies[index].favorit)"
                ></i>
              </div>
              <div v-else>
                <i
                  class="fa fa-star-o star-favorite"
                  style="font-size: 1.8rem; color: white"
                  @click="addFavoritMovie(index, movies[index].favorit)"
                ></i>
              </div>
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
      favoritMovies: 0,
    };
  },
  methods: {
    //sorting algorithms ascending and descending by movie name (Alphabet)
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

    //sorting algorithms ascending and descending by Movie Rating
    sortRating() {
      if (this.ascRating) {
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

    //add starred movie to a list of favorites/liked.
    addFavoritMovie(id, favorit) {
      if (favorit) {
        this.movies[id].favorit = false;
      console.log(this.movies[id])
        this.favoritMovies--;
      } else {
        this.movies[id].favorit = true;
        this.favoritMovies++;
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
  font-family: "Source Sans Pro Bold";
  text-transform: uppercase;
}
h2 {
  text-align: left;
  color: white;
  background: #171717;
}

.movies-header{
  padding-left: 5%;
}

h1,
h2 {
  margin-bottom: 0 !important;
  padding: 1rem;
}
.movie-container {
  background: #1d1d1d;
  text-align: center;
  padding-top: 2rem;
}

.movie-card {
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
  text-align: left;
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
.rating-overlay {
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

.rating-container:hover .rating-overlay,
.star-favorite {
  opacity: 1;
  width: 100%;
  color: white;
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

.favorit-movies{
  padding-left: 0.5rem;
}

.sort-movies {
  color: white;
}
.sort-movies > p {
  font-size: 0.95rem;
  background: #131313;
  margin: 0;
  padding: 0;
  color: white;

  position: absolute;
  opacity: 0.5;
  left: 70.07%;
  right: 19.44%;
  top: 8.95%;
  bottom: 85.13%;
}

.sort-title,
.sort-rating {
  color: white;
  box-sizing: border-box;
  position: absolute;
  background: #131313;
  border: 1px solid #2e2e2e;
  border-radius: 6px;
}

.sort-title {
  left: 70.07%;
  right: 19.44%;
  top: 12%;
  bottom: 84.53%;
}
.sort-rating {
  left: 82.64%;
  right: 6.88%;
  top: 12%;
  bottom: 84.53%;
}

.star-favorite {
  position: absolute;
  left: 38%;
  top: 5%;
}
.star-header {
  font-size: 1.3rem;
  color: white;
  position: absolute;
  left: 95%;
  top: 5%;
  
  display: inline-block;
}
i {
  font-size: 1.8rem;
}

@media only screen and (max-width: 800px) {

  .star-header {
    left: 90%;
  }
}
</style>
