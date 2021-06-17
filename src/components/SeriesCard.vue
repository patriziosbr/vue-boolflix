<template>
  <section>
    <div class="rosicato">

    <div class="posterUp"> 
        <img class="poster" :src="getPoster()"  @error="replaceByDefault" alt="">   
    </div>
    

    <div class="detailsUp mb-auto">

        <h1 class="detailsUph1"> {{ itemSerie.name }} </h1> 
        <h2 class="detailsUph2" :class="(itemSerie.name === itemSerie.original_name) ? 'hide' : 'show' " > {{ itemSerie.original_name }} </h2>
        <img class="flag" src="../assets/images/en.png" alt="eng flag" v-if="itemSerie.original_language == 'en'">
        <img class="flag" src="../assets/images/it.png" alt="ita flag" v-else-if="itemSerie.original_language == 'it'">
        <p class="detailsUpp" v-else> {{ itemSerie.original_language }} </p>
        <div class="mb-auto">
            <i v-for="i in 5" :key="i" :class="i <= starCount(itemSerie) ? 'fas fa-star' : 'far fa-star'"></i>
        </div>
        
    </div>

    </div> 
    <!-- rosicato -->
  
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
            img404: 'https://cdn.iconscout.com/icon/premium/png-256-thumb/404-5-1136227.png'
        }
    },
    methods:{
        getPoster() {
            return this.path + this.itemSerie.poster_path;
        },
        replaceByDefault(e) {
            console.log("404 gestito in serie");
            e.target.src = require("../assets/images/notFound.png")
        },
        starCount(item) {
            return Math.ceil(item.vote_average / 2);
        }
    }
}
</script>

<style lang="scss" >

   
</style>