<template>
<div>
  <header id="site_header">
    <div class="container">
      <div class="logo">
        <h2>BOOLFLIX</h2>
        // eslint-disable-next-line vue/no-parsing-error
        <SearchBar @searchMovies="getMovie"/>
      </div>
    </div>
    <!-- /.container -->
  </header>
  <!-- /#site_header -->
  <main id="site_main">
    <div class="container">
      <div class="movies_series" >
        <div class="movie" v-for="movie in movies" :key="movie.id">
          <div class="jumbo" v-if="movie.poster_path !== null">
            <img class="poster"
              :src="'http://image.tmdb.org/t/p/w342' + movie.poster_path"
              :alt="movie.title"
            />
            <div class="info">
            <div class="specifications">
            <h3>Title: {{ movie.title }}</h3>
            <h4>
              Original title: {{ movie.original_title }}
            </h4>
            <div class="languages">
              <p><strong>Language: </strong></p>
              <div class="flag">
                <img class="icon_flag"
                  :src="movie.original_language"
                  :alt="movie.original_language"
                  width="25"
                />
              </div>
            </div>
            <!-- /.languages -->
            <div v-if="movie.vote_average >= 1">
              <p>
                <strong>Vote: </strong>
                <i
                  class="stars"
                  :class="classStars"
                  v-for="index in movie.vote_average"
                  :key="index.id"
                ></i>
              </p>
            </div>
            <div v-else>
              <p><strong> Vote: </strong>{{ movie.vote_average }}</p>
            </div>
               <p v-if="movie.overview !== ''"><strong>Overview:</strong> {{movie.overview}}</p>
                <div class="cast" v-for="cast in casts" :key="cast.id">
                 <p v-if="movie.id === id">Cast: {{cast.name}}</p>
               </div>
            </div>
          <!-- /.specifications -->
          </div>
          <!-- /.info -->
          </div>
          <div v-else class="jumbo">
            <h3 class="avaiable">IMAGE NOT AVAIABLE</h3>
            <div class="info">
              <div class="specifications">
            <h3>Title: {{ movie.title }}</h3>
            <h4>
              Original title: {{ movie.original_title }}
            </h4>
            <div class="languages">
              <p> <strong>Language: </strong></p>
              <div class="flag">
                <img class="icon_flag"
                  :src="movie.original_language"
                  :alt="movie.original_language"
                  width="25"
                />
              </div>
            </div>
            <!-- /.languages -->
            <div v-if="movie.vote_average >= 1">
              <p>
                <strong>Vote: </strong>
                <i
                  class="stars"
                  :class="classStars"
                  v-for="index in movie.vote_average"
                  :key="index.id"
                ></i>
              </p>
            </div>
            <div v-else>
              <p><strong>Vote: </strong> {{ movie.vote_average }}</p>
            </div>
             <p v-if="movie.overview !== ''"><strong>Overview:</strong> {{movie.overview}}</p>
              <div class="cast" v-for="cast in casts" :key="cast.id">
                 <p v-if="movie.id === id">Cast: {{cast.name}}</p>
              </div>
            </div>
          <!-- /.specifications -->
          </div>
          </div>
          <!-- /.jumbo -->
          <button @click='searchMovieCast(movie.id)'>Search cast</button>
        </div>
        <!-- /.movie -->
          <div class="serie" v-for="serie in series" :key="serie.id">
          <div class="jumbo" v-if="serie.poster_path !== null">
            <img class="poster"
              :src="'http://image.tmdb.org/t/p/w342' + serie.poster_path"
              :alt="serie.name"
            />
            <div class="info">
            <div class="specifications">
            <h3>Title: {{ serie.name }}</h3>
            <h4>
              Original title: {{ serie.original_name }}
            </h4>
            <div class="languages">
              <p><strong>Language: </strong></p>
              <div class="flag">
                <img class="icon_flag"
                  :src="serie.original_language"
                  :alt="serie.original_language"
                  width="25"
                />
              </div>
            </div>
            <!-- /.languages -->
            <div v-if="serie.vote_average >= 1">
              <p>
                <strong>Vote: </strong>
                <i
                  class="stars"
                  :class="classStars"
                  v-for="index in serie.vote_average"
                  :key="index.id"
                ></i>
              </p>
            </div>
            <div v-else>
              <p><strong> Vote: </strong>{{ serie.vote_average }}</p>
            </div>
               <p v-if="serie.overview !== ''"><strong>Overview:</strong> {{serie.overview}}</p>
              <div class="cast" v-for="cast in casts" :key="cast.id">
                 <p v-if="serie.id === id">Cast: {{cast.name}}</p>
              </div>
            </div>
          <!-- /.specifications -->
          </div>
          </div>
          <div v-else class="jumbo">
            <h3 class="avaiable">IMAGE NOT AVAIABLE</h3>
            <div class="info">
              <div class="specifications">
            <h3>Title: {{ serie.name }}</h3>
            <h4>
              Original title: {{ serie.original_name }}
            </h4>
            <div class="languages">
              <p> <strong>Language: </strong></p>
              <div class="flag">
                <img class="icon_flag"
                  :src="serie.original_language"
                  :alt="serie.original_language"
                  width="25"
                />
              </div>
            </div>
            <!-- /.languages -->
            <div v-if="serie.vote_average >= 1">
              <p>
                <strong>Vote: </strong>
                <i
                  class="stars"
                  :class="classStars"
                  v-for="index in serie.vote_average"
                  :key="index.id"
                ></i>
              </p>
            </div>
            <div v-else>
              <p><strong>Vote: </strong> {{ serie.vote_average }}</p>
            </div>
             <p v-if="serie.overview !== ''"><strong>Overview:</strong> {{serie.overview}}</p>
             <div class="cast" v-for="cast in casts" :key="cast.id">
                 <p v-if="serie.id === id">Cast: {{cast.name}}</p>
               </div>
            </div>
          <!-- /.specifications -->
          </div>
          </div>
          <!-- /.jumbo -->
          <button @click='searchSerieCast(serie.id)'>Search cast</button>
        </div>
        <!-- /.serie -->
        <h5>{{ problem }}</h5>
      </div>
      <!-- /.movies_series -->
    </div>
    <!-- /.container -->
  </main>
  <!-- /#site_main -->
</div>

</template>

<script>
import axios from 'axios'
import SearchBar from '../components/SearchBar.vue'
/* import SiteHeader from '../components/SiteHeader.vue' */
export default {
  components: {
    SearchBar
  },

  data () {
    return {
      movies: [],
      series: [],
      problem: '',
      flags: [
        {
          chiave: 'en',
          image: 'https://images.emojiterra.com/twitter/512px/1f1ec-1f1e7.png'
        },
        {
          chiave: 'it',
          image: 'https://images.emojiterra.com/twitter/512px/1f1ee-1f1f9.png'
        }
      ],
      countryCode: '',
      status: '',
      classStars: 'fas fa-star',
      digitText: '',
      id: '',
      casts: []
    }
  },
  methods: {
    getMovie (textInput) {
      this.digitText = textInput
      this.callApi()
    },
    callApi () {
      axios
        // eslint-disable-next-line quotes
        .get('https://api.themoviedb.org/3/search/movie?api_key=2c70cf7212141e650767768ea94e23e6&language=en-US&query=' + this.digitText + "&page=1&include_adult=false")
        .then((response) => {
          // console.log(response)
          this.movies = response.data.results
          this.flagsLanguage(this.movies)
        })
        .catch((error) => {
          // console.log(error)
          this.problem = error
          this.movies = ''
          console.log(this.problem)
        })
      axios
        // eslint-disable-next-line quotes
        .get('https://api.themoviedb.org/3/search/tv?api_key=2c70cf7212141e650767768ea94e23e6&language=en-US&page=1&include_adult=false&query=' + this.digitText)
        .then((response) => {
          // console.log(response)
          this.series = response.data.results
          this.flagsLanguage(this.series)
        })
        .catch((error) => {
          // console.log(error)
          this.problem = error
          this.series = ''
          console.log(this.problem)
        })
    },
    resetText () {
      this.digitText = ''
      console.log(this.digitText)
    },
    flagsLanguage (listOfFlags) {
      listOfFlags.forEach(flag => {
        this.iconsNations(flag)
        this.changeVotes(flag)
      })
      return listOfFlags
    },
    iconsNations (icon) {
      this.flags.forEach(element => {
        // console.log(element)
        if (icon.original_language === element.chiave) {
          icon.original_language = element.image
        }
      })
    },
    changeVotes (item) {
      item.vote_average = Math.round(item.vote_average)
      if (item.vote_average === 10 || item.vote_average === 9) {
        item.vote_average = 5
      } else if (item.vote_average === 8 || item.vote_average === 7) {
        item.vote_average = 4
      } else if (item.vote_average === 6 || item.vote_average === 5) {
        item.vote_average = 3
      } else if (item.vote_average === 4 || item.vote_average === 3) {
        item.vote_average = 2
      } else if (item.vote_average === 2 || item.vote_average === 1) {
        item.vote_average = 1
      }
    },
    searchMovieCast (id) {
      this.id = id
      axios
        // eslint-disable-next-line quotes
        .get(`https://api.themoviedb.org/3/movie/${this.id}/credits?api_key=2c70cf7212141e650767768ea94e23e6&language=en-US`)
        .then((response) => {
          // console.log(response)
          this.casts = response.data.cast
          this.casts = this.casts.slice(0, 5)
          this.flagsLanguage(this.movies)
        })
        .catch((error) => {
          // console.log(error)
          this.problem = error
        })
    },
    searchSerieCast (id) {
      this.id = id
      console.log(id)
      axios
        // eslint-disable-next-line quotes
        .get(`https://api.themoviedb.org/3/tv/${this.id}/credits?api_key=2c70cf7212141e650767768ea94e23e6&language=en-US`)
        .then((response) => {
          // console.log(response)
          this.casts = response.data.cast
          this.casts = this.casts.slice(0, 5)
          this.flagsLanguage(this.series)
        })
        .catch((error) => {
          // console.log(error)
          this.problem = error
        })
    }
  }
  /*  mounted: function () {
    this.flagsLanguage()
  } */

}
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";
header {
  height: 100px;
  background-color: $bg_base;
  .logo {
    line-height: 100px;
    h2 {
      color: $color_logo;
      padding-left: 1rem;
    }
  }
}
#site_main {
  .movies_series {
    display: flex;
    flex-wrap: wrap;
    .movie, .serie {
    padding: 1rem;
    width: calc(100% / 3);
    height: 650px;
    margin-top: 1rem;

    .jumbo {
      height: 100%;
      border: 1px solid $bg_base;
      position: relative;
      .avaiable {
        text-align: center;
        vertical-align: middle;
        line-height: 500px;
      }
    }
    .jumbo:hover .info{
     visibility: visible;
     cursor: pointer;
    }
    .poster {
        height: 100%;
        width: 100%;
        object-fit: cover;
        display: block;
    }
    .info {
      visibility: hidden;
      height: calc(100% - 83.89px);
      border: 1px solid $bg_base;
      width: 100%;
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      background-color: $bg_base;
      overflow: auto;

      .specifications {
        color: #fff;
        padding: 1rem;
      }
    }
    .languages {
      display: flex;
      align-items: center;
      .icon_flag {
        margin-left: 0.5rem ;
      }
    }
    .stars {
      color: $color_average;
    }
  }
  }

}

</style>
