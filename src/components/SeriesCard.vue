<template>
  <section>
    
    <li> 
        <img class="poster" :src="getPoster()" alt="">      
        <p> {{ itemSerie.name }} </p> 
        <p> {{ itemSerie.original_name }} </p>
        <img class="flag" src="../assets/images/en.png" alt="eng flag" v-if="itemSerie.original_language == 'en'">
        <img class="flag" src="../assets/images/it.png" alt="ita flag" v-else-if="itemSerie.original_language == 'it'">
        <p v-else> {{ itemSerie.original_language }} </p>
        <p> {{ itemSerie.vote_average }} </p>
    </li>
  
  </section>

</template>

<script>
export default {
    name: "SeriesCard",
    props: [ "itemSerie" ],
    // aggiungere data...
    data() {
        return {
            path: 'https://image.tmdb.org/t/p/w342',
            // path404: 'https://image.tmdb.org/t/p/w342null',
            // img404: 'https://cdn.iconscout.com/icon/premium/png-256-thumb/404-5-1136227.png'
        }
    },
    methods:{
        getPoster() {
            // if ( this.path404 ) {
            //     this.path = this.img404
            // }
            return this.path + this.itemSerie.poster_path
        }
    }
}
</script>

<style lang="scss" >
   
</style>