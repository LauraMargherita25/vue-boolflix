<template>
  <div id="app">
    <file-header @search="searchString($event)"/>
    <file-main :arrMovies="arrMovies"/>
  </div>
</template>

<script>
import axios from "axios"
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
      arrMovies: null,
    }
  },

  methods: {
    searchString(str) {
      if (str == "") {
        return
      }
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=b653bf3e070940e3fc3715a2e87ee7db&language=it-IT&query=' + str)
      .then(response => {
        console.log(response);
        this.arrMovies = response.data.results;
      })
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
