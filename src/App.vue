<template>
  <div id="app">
      <!-- removed @sonBox="inputMethod" -->
      <Navbar  @myFilterBtn="btnMethod($event)" />

      <div v-if="queryBox.length == 0">
        <h1>search a movie</h1>
      </div>
      <MainMovies :moviesArr="movies" v-else />
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
      movies: [],
      queryBox: "",
    }
  },
  components: {

    Navbar,
    MainMovies

  },
  created: function() {
    this.loadMovies();
  },
  methods: {
    loadMovies : function() {
      axios.get(this.moviesApi, { 
        params: {
        api_key: '8a1eb2b52d478a483e4e91c6971f7e85',
        query: 'this.queryBox',
        language: 'it-IT'
      }}).then ( (resp) => {
        this.movies = resp.data.results;
      }).catch(e => {
        console.log(e)
      })
    },
    btnMethod(option) {
      
      this.queryBox = option;

      this.movies.includes(this.queryBox);
      
      console.log(this.queryBox);
    }

  }

}
</script>

<style lang="scss">

</style>
