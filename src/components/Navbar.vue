<template>
  <section class="topnav container-fluid fixed-top">
      
      <div class="row d-flex justify-content-between align-items-center">

        <div class="logodebug col-md-2">
            <a href="http://localhost:8080">
                <img  class="imgLogo" src="../assets/images/logo.png" alt="">
            </a>
        </div>
  
      
        <div class=" col-md-3">
            <input v-model="searchBox" type="text" @keyup.enter="filterBtn(searchBox) " placeholder="Search here">
            <div>
                <div class=" col-md-12">   
                    <button @click="filterBtn(searchBox);">Search</button>
                </div>
            </div>
        </div>


      
      </div>

  </section>
</template>

<script>
export default {
    name: "Navbar",
    data() {
        return {
            searchBox : ''
        }
    },
    methods: {
        filterBtn(event) {
            return this.$emit( "myFilterBtn", event );
        }
    }
}
</script>

<style lang="scss" scoped>
@import 'bootstrap/scss/_functions.scss';
@import 'bootstrap/scss/_variables.scss';
@import 'bootstrap/scss/_mixins.scss';

    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    .topnav {
        max-height: 250px;
        padding: 24px;
        background-color: #333;
        
        .logodebug {
            text-align: center;
            height: 60px;
            margin-bottom: 8px;

            img.imgLogo {
                height: 100%;
            }
            
        }
        input,
        button {
            width: 100%;
            padding: 8px 32px;
            border-radius: 5px;
            margin: 4px 0;
            color: rgb(124, 124, 124);
        }
    
    @include media-breakpoint-up(sm) { 
        
        .logodebug {
            text-align: start;
        }

     }
     
    }
</style>