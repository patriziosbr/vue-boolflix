<template>
  <section >
       <div >
        <div class="posterUp">
            <img class="poster" :src="getPoster()" @error="replaceByDefault" alt="">   
        </div>


        <div class="detailsUp mb-auto">
            
            <h1 class="detailsUph1"> {{ itemMovie.title }} </h1>
            <h2 class="detailsUph2" :class="(itemMovie.title === itemMovie.original_title) ? 'hide' : 'show' " > {{ itemMovie.original_title }} </h2>
            <img class="flag" src="../assets/images/en.png" alt="eng flag" v-if="itemMovie.original_language == 'en'">
            <img class="flag" src="../assets/images/it.png" alt="ita flag" v-else-if="itemMovie.original_language == 'it'">
            <p class="detailsUpp" v-else>{{ itemMovie.original_language }}</p>
            <p class="trama"> {{ itemMovie.overview }} </p>
            <div class="mb-auto">
                <i v-for="i in 5" :key="i" :class="i <= starCount(itemMovie) ? 'fas fa-star' : 'far fa-star'"></i>
            </div>

        </div> 

       </div> 
       <!-- rosicato -->


  </section>
</template>

<script>


export default {
    name: "MovieCard",
    props: [ "itemMovie" ],
    data() {
        return {
            path: 'https://image.tmdb.org/t/p/w342',
            img404: "../assets/images/notFound.png"
        }
    },
    methods:{
        getPoster() {
            return this.path + this.itemMovie.poster_path
        },
        replaceByDefault(e) {
            console.log("404 gestito in movies");
            e.target.src = require("../assets/images/notFound.png")
        },
        starCount(item) {
            return Math.ceil(item.vote_average / 2);
        }
    }
}
</script>

<style lang="scss" >
    .trama {
        font-size: 11px;
        width: 111px;
        height: 61px;
        white-space: wrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }
</style>
