<template>
  <div id="app">

      <Navbar  />

      <MainMovies :moviesArr="movies" />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Navbar from './components/Navbar.vue';
import MainMovies from './components/MainMovies.vue';
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      moviesApi: "https://api.themoviedb.org/3/search/movie",
      movies: []
    }
  },
  components: {

    Navbar,
    MainMovies

  },
  mounted: function() {
    this.loadMovies();
    console.log(this.movies);
  },
  methods: {
    loadMovies : function() {
      axios.get(this.moviesApi, { 
        params: {
        api_key: '8a1eb2b52d478a483e4e91c6971f7e85',
        query: "pro",
        language: 'it-IT'
      } }).then ( (resp) => {
        
        this.movies = resp.data.results;
      } )
    }
  }

}
</script>

<style lang="scss">

</style>
