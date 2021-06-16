<template>
  <section>
       
        <li>
            <img class="poster" :src="getPoster()" @error="replaceByDefault" alt="">   
            <p>{{ itemMovie.title }}</p>
            <p>{{ itemMovie.original_title }}</p>
            <img class="flag" src="../assets/images/en.png" alt="eng flag" v-if="itemMovie.original_language == 'en'">
            <img class="flag" src="../assets/images/it.png" alt="ita flag" v-else-if="itemMovie.original_language == 'it'">
            <p v-else>{{ itemMovie.original_language }}</p>
            <span>
                <i v-for="i in 5" :key="i" :class="i <= starCount(itemMovie) ? 'fas fa-star' : 'far fa-star'"></i>
            </span>
        </li> 

  </section>
</template>

<script>


export default {
    name: "MovieCard",
    props: [ "itemMovie" ],
    data() {
        return {
            path: 'https://image.tmdb.org/t/p/w342',
            img404: 'https://cdn.iconscout.com/icon/premium/png-256-thumb/404-5-1136227.png'
        }
    },
    methods:{
        getPoster() {
            return this.path + this.itemMovie.poster_path
        },
        replaceByDefault(e) {
            console.log("404 gestito in movies");
            e.target.src = this.img404
        },
        starCount(item) {
            return Math.ceil(item.vote_average / 2);
        }
    }
}
</script>

<style lang="scss" >

    
</style>
