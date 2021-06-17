<template>
  <section class="container-fluid main-movies">

    <h1> {{ startSearch() }}</h1>
    <h1> {{ resultsWarn() }}</h1>


    <h2 v-if=" moviesArr.length === 0 && seriesArr.length > 1 " >Movies</h2>
    <h2 v-else-if="moviesArr.length > 0">MovieS</h2>
    <h1> {{ moviesWarn() }}</h1>

    

      <div class="clearfix">
        <MovieCard v-for="movie in moviesArr" :key="movie.id" :itemMovie="movie" class="float-start movie-serie-item"/>
      </div>

    
    
    <h2 v-if=" moviesArr.length > 1 && seriesArr.length === 0 "> Serie Tv</h2>
    <h2 v-else-if="seriesArr.length > 0">Serie TV</h2>
    <h1> {{ seriesWarn() }}</h1>

    <ul>
      <SeriesCard v-for="serie in seriesArr" :key="serie.id" :itemSerie="serie"/>
    </ul>

  </section>
</template>

<script>
import MovieCard from './MovieCard.vue'
import SeriesCard from './SeriesCard.vue'

export default {
  name: "MainMovies",
  props: [ "moviesArr", "seriesArr", "queryString" ],
  data() {
    return {
      searchMovie:"Search a movie",
      noMoviesFound: "No Movies Found",
      noSeriesFound: "No Series Found",
      noResultsFound: "No Series or movies Found"
    }
  },
  methods: {
    startSearch() {
      if( this.queryString.length == " " && this.queryString.length == 0 && this.moviesArr.length == 0 && this.seriesArr.length == 0 ) {
        return this.searchMovie
      }
    },
    moviesWarn() {
      if( this.queryString.length > 1 && this.moviesArr.length == 0 &&this.seriesArr.length > 1) {
      return this.noMoviesFound
      }
    },
    seriesWarn() {
      if( this.queryString.length > 1 && this.moviesArr.length > 1 && this.seriesArr.length == 0) {
      return this.noSeriesFound
      }
    },
    resultsWarn() {
      if( this.queryString.length > 1 && this.moviesArr.length == 0 && this.seriesArr.length == 0) {
      return this.noResultsFound
      }
    }
  },
  components: { 
    MovieCard,
    SeriesCard
  }
}
</script>

<style lang="scss">
@import 'bootstrap/scss/_functions.scss';
@import 'bootstrap/scss/_variables.scss';
@import 'bootstrap/scss/_mixins.scss';

  .main-movies {
    min-height: 100vh;
    padding-top: 250px;
    background-color: rgb(20, 20, 20);

    .movie-serie-item {
      width: calc(100% / 3);
      padding: 0 2px;
      img.poster {
        width: 100%;
      }
    }
  }

  

    .flag {
      height: 30px;
    }

    .hide {
      display: none;
    }
    .show {
      display: block;
    }

    @include media-breakpoint-up(md) {  

        .main-movies {
          padding-top: 160px;

          .movie-serie-item {
             width: calc(100% / 5);
             padding: 0 4px;
          }
        }

     }
</style>