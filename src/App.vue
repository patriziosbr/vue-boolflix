<template>
  <div id="app">
      <Navbar  @myFilterBtn="btnMethod($event)" />

      <MainMovies :moviesArr="movies" :seriesArr="series"/>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import MainMovies from './components/MainMovies.vue';
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      moviesApi: "https://api.themoviedb.org/3/search/movie",
      tvApi: "https://api.themoviedb.org/3/search/tv",
      api_keyData: '8a1eb2b52d478a483e4e91c6971f7e85',
      languageData: 'it-IT',
      movies: [],
      series: [],
      queryBox: "",
      searchMovie: "search a movie"
    }
  },
  components: {
    Navbar,
    MainMovies
  },
  methods: {
    loadMovies : function() {
      axios.get(this.moviesApi, { 
        params: {
        api_key: this.api_keyData,
        query: this.queryBox,
        language: this.languageData,
      }}).then ( (resp) => {
        this.movies = resp.data.results;
      }).catch(e => {
        console.log("errore in movies", e)
      })
    },
    loadSeries: function() {
      axios.get(this.tvApi, {
        params: {
          api_key: this.api_keyData,
          query: this.queryBox,
          language: this.languageData
        }}).then ( (res) => {
          this.series = res.data.results
        }).catch( e => {
          console.log("errore in serie", e);
        })
    },
    btnMethod(option) {
      this.queryBox = option;
      this.loadMovies();
      this.loadSeries();
    }

  }

}
</script>

<style lang="scss">

</style>
