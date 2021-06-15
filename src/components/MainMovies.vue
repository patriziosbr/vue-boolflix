<template>
  <section>

    <h1>Movies</h1>
    <ul>
      <MovieCard v-for="movie in moviesArr" :key="movie.id" :itemMovie="movie"/>
    </ul>

    <h2>Serie Tv</h2>
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
  props: [ "moviesArr", "seriesArr" ],
  components: { 
    MovieCard,
    SeriesCard
  }
}
</script>

<style lang="scss">
   .poster {
        width: 25%;
    }
    .flag {
        height: 30px;
    }
</style>