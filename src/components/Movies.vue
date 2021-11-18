<template>
  <div class="container">
    <div class="search_bar">
      <input v-model="search" type="text">
    <button @click="callApi(search)">Search movie</button>
    </div>
    <div class="movies">
      <div class="movie" v-for="movie in movies" :key="movie.id">
      <div class="specifications_movie">
          <h4>Title: {{movie.title}}</h4>
          <h5>Original title: {{movie.original_title}}</h5>
          <p>Language: {{movie.original_language}}</p>
          <p>Vote: {{movie.vote_average}}</p>
      </div>
    </div>
    <h5>{{problem}}</h5>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      search: '',
      movies: [],
      problem: ''
    }
  },
  methods: {
    getMovie (textInput) {
      this.search = textInput
      // console.log(this.search)
    },
    callApi () {
      this.getMovie(this.search)
      axios
        // eslint-disable-next-line quotes
        .get('https://api.themoviedb.org/3/search/movie?api_key=2c70cf7212141e650767768ea94e23e6&language=en-US&query=' + this.search + "&page=1&include_adult=false")
        .then((response) => {
          // console.log(response)
          this.movies = response.data.results
          // console.log(this.movies)
        })
        .catch((error) => {
          // console.log(error)
          this.problem = error
          this.movies = ''
          console.log(this.problem)
        })
      this.search = ''
    }

  }
}
</script>

<style lang="scss">
.container {
  max-width: 1200px;
  margin: 2rem auto;
  .search_bar {
    display: flex;
    justify-content: center;

    input {
      margin-right: 1rem;
    }
  }
  .movie {
    padding: 1rem;
  }
}
</style>
