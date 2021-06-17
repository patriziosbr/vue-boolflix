<template>
  <section class="container-fluid main-movi-seri">

    <h1> {{ startSearch() }}</h1>
    <h1 class="warn"> {{ resultsWarn() }}</h1>


    <h2 v-if=" moviesArr.length === 0 && seriesArr.length > 1 " >Movies</h2>
    <h2 v-else-if="moviesArr.length > 0">MovieS</h2>
    <h1 class="warn"> {{ moviesWarn() }}</h1>

    

      <div class="clearfix">
        <MovieCard v-for="movie in moviesArr" :key="movie.id" :itemMovie="movie" class="float-start movie-serie-item "/>
      </div>

    
    
    <h2 v-if=" moviesArr.length > 1 && seriesArr.length === 0 "> Serie Tv</h2>
    <h2 v-else-if="seriesArr.length > 0">Serie TV</h2>
    <h1 class="warn"> {{ seriesWarn() }}</h1>

    <div class="clearfix">
      <SeriesCard v-for="serie in seriesArr" :key="serie.id" :itemSerie="serie" class="float-start movie-serie-item d-flex flex-column" />
    </div>

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

  .main-movi-seri {
    min-height: 100vh;
    padding-top: 250px;
    background-color: rgb(20, 20, 20);

    .movie-serie-item {
      
      width: calc(100% / 3);
      min-height: 380px;
      padding: 0 2px;

      img.poster {
        width: 100%;
      }

      .posterUp {
        
        margin-bottom: 8px;
      }
 
    }

  }
  //testi per serie e film mobile
  .detailsUp {
   
    text-align: center;

    .detailsUph1 {
        font-size: 13px;
        font-weight: 700;
    }
    .detailsUph2 {
        font-size: 11px;
        font-weight: 900;
        color: rgb(130, 130, 130);
    }
    .detailsUpp {
        
        font-size: 10px;
    }
}
    .warn {
      font-size: 18px;
      padding-bottom: 24px;
    }
    .flag {
      height: 30px;
      margin: 8px 0;
    }

    .hide {
      display: none;
    }
    .show {
      display: block;
    }

    @include media-breakpoint-up(md) {  

        .main-movi-seri {
          padding-top: 160px;

          .movie-serie-item {
             width: calc(100% / 5 - 9px) ;
             padding: 0 4px;
             position: relative;
          }

        }
        .detailsUp {
          display: none;
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          
        }
        // soluzione poster hidden
        .movie-serie-item:hover .detailsUp {
          display: block;
        }
        .movie-serie-item:hover .posterUp {
            visibility: hidden;
        }
        // soluzione rgba
          // .movie-serie-item:hover .detailsUp {
          //   display: block;
          //   width: 100%;
          //   height: 100%;
          //   background-color: rgba(0,0,0,0.9);
          // }

    }
</style>