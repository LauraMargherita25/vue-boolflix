<template>
  <div id="app">
    <file-header @search="searchString"/>
    <file-main :search-data="strToSearch"/>
  </div>
</template>

<script>
import FileHeader from './components/FileHeader.vue'
import FileMain from './components/FileMain.vue'

export default {
  name: 'App',

  components: {
    FileHeader,
    FileMain
  },

  data() {
    return {
      strToSearch: "",
    }
  },

  methods: {
    searchString(strToSearch) {
      this.strToSearch = strToSearch;
    }
  }
  
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
@import "./assets/styles/style.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
