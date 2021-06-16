<template>
  <section>
    <h1 v-if="moviesArr.length == 0 && seriesArr.length == 0"> fai una ricerca </h1>
    <h2 v-if="(payload > 1 && moviesArr.length == 0 && seriesArr.length == 0 )">Ritenta</h2>
    <div v-if="moviesArr.length > 0">
      <h1>Movies</h1>
      <ul>
        <MovieCard v-for="movie in moviesArr" :key="movie.id"   :itemMovie="movie"/>
      </ul>
    </div>

    <div v-if="seriesArr.length > 0">
      <h2>Serie Tv</h2>
      <ul>
        <SeriesCard v-for="serie in seriesArr" :key="serie.id" :itemSerie="serie"/>
      </ul>
    </div>

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
@import '~@fortawesome/fontawesome-free/css/all.min.css';

   .poster {
        width: 25%;
    }
    .flag {
        height: 30px;
    }
</style>