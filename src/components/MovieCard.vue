<template>
  <section>
       
        <li>
            <img class="poster" :src="getPoster()" alt="">   
            <p>{{ itemMovie.title }}</p>
            <p>{{ itemMovie.original_title }}</p>
            <img class="flag" src="../assets/images/en.png" alt="eng flag" v-if="itemMovie.original_language == 'en'">
            <img class="flag" src="../assets/images/it.png" alt="ita flag" v-else-if="itemMovie.original_language == 'it'">
            <p v-else>{{ itemMovie.original_language }}</p>
            <p>{{ itemMovie.vote_average }}</p>
        </li> 

  </section>
</template>

<script>
export default {
    name: "MovieCard",
    props: [ "itemMovie" ],
    data() {
        return {
            path: 'https://image.tmdb.org/t/p/w342'
        }
    },
    methods:{
        getPoster() {
            return this.path + this.itemMovie.poster_path
        }
    }
}
</script>

<style lang="scss" >
    
</style>
