<template>
  <section>
    <h1>Movies</h1>
    <ul>
      <MovieCard v-for="movie in moviesArr" :key="movie.id" :itemMovie="movie"/>
    </ul>

    <ul>
      <SeriesCard />
    </ul>

  </section>
</template>

<script>
import MovieCard from './MovieCard.vue'

export default {
  name: "MainMovies",
  props: [ "moviesArr", "seriesArr" ],
  components: { 
    MovieCard 
  }
}
</script>

<style>

</style>