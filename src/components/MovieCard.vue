<template>
  <section>
       
        <li>
            <img class="poster" :src="getPoster()" alt="">   
            <p>{{ itemMovie.title }}</p>
            <p>{{ itemMovie.original_title }}</p>
            <img class="flag" src="../assets/images/en.png" alt="eng flag" v-if="itemMovie.original_language == 'en'">
            <img class="flag" src="../assets/images/it.png" alt="ita flag" v-else-if="itemMovie.original_language == 'it'">
            <p v-else>{{ itemMovie.original_language }}</p>
            <span v-for="(star, index) in stars" :key="index" v-html="star"> {{ displayStar(itemMovie.vote_average) }} </span>
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
            fullStar: '<i class="fas fa-star"></i>',
            emptyStar: '<i class="far fa-star"></i>',
            stars: []
        }
    },
    methods:{
        getPoster() {
            return this.path + this.itemMovie.poster_path
        },
        displayStar(avgVote) {
            let vote = avgVote/2;
            let fixedVote = Math.ceil(vote)
            console.log(fixedVote);

            while(this.stars.length < 5) {
                
                // for(let i = 0; i <= fixedVote; i++ ) {
                //  this.stars.length.push(this.fullStar)
                
                // }
                // this.stars.length.push(this.emptyStar)
                if ( this.stars.length < fixedVote) {

                    for(let i = 0; i < fixedVote; i++ ) {

                        this.stars.push(this.fullStar)
                    }
                } else {
                    this.stars.push(this.emptyStar)
                }
            }
        }

    }
}
</script>

<style lang="scss" >
@import '~@fortawesome/fontawesome-free/css/all.min.css'
    
</style>
