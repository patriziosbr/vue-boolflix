<template>
  <section>
       
        <li>
            <p>{{ itemMovie.title }}</p>
            <p>{{ itemMovie.original_title }}</p>
            <img src="../assets/images/en.png" alt="eng flag" v-if="itemMovie.original_language == 'en'">
            <img src="../assets/images/it.png" alt="ita flag" v-else-if="itemMovie.original_language == 'it'">
            <p v-else>{{ itemMovie.original_language }}</p>
            <p>{{ itemMovie.vote_average }}</p>
        </li> 
  </section>
</template>

<script>
export default {
    name: "MovieCard",
    props: [ "itemMovie" ]
}
</script>

<style lang="scss" scoped>
    img {
        height: 30px;
    }
</style>
