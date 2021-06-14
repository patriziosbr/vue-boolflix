<template>
  <section class="topnav">
      <div class="logodebug">
          This is a logo
      </div>
      <div>
        <input v-model="searchBox" type="text">
        <button @click="filterBtn(searchBox)">Search</button>
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
    .topnav {
        max-width: 1170px;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        padding: 24px;
        background-color: #333;
        
        .logodebug {
            color: red;
        }
    }
</style>