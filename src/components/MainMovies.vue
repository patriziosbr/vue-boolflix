<template>
  <section>
      <ul>
          <!-- removed @myList="$emit('thisList', movie)" -->
        <li v-for="movie in moviesArr" :key="movie.id" >
        <p>{{ movie.title }}</p>
        <p>{{ movie.original_title }}</p>
        <p>{{ movie.original_language }}</p>
        <p>{{ movie.vote_average }}</p>

        </li> 

      </ul>
  </section>
</template>

<script>
export default {
    name: "MainMovies",
    props: [ "moviesArr" ]
}
</script>

<style>

</style>