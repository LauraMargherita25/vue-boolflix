<template>
  <div id="app">
    <file-header @search="searchString"/>
    <file-main :arrMovies="arrMovies" :arrSeries="arrSeries"/>
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
      apiUrl: 'https://api.themoviedb.org/3/',
      apiKey: 'b653bf3e070940e3fc3715a2e87ee7db',
      arrMovies: [],
      arrSeries: [],
    }
  },

  methods: {
    searchString(str) {

      if (str == "") {
        return
      }
      // ricerca film
      axios.get(this.apiUrl + 'search/movie', {
        params: {
          api_key: this.apiKey,
          lang: 'it-IT',
          query: str,
        }
      })
      .then(response => this.arrMovies = response.data.results)

      // ricerca serie
      axios.get(this.apiUrl + 'search/tv', {
        params: {
          api_key: this.apiKey,
          lang: 'it-IT',
          query: str,
        }
      })
      .then(response => this.arrSeries = response.data.results)

      /* if (str == "") {
        return
      }
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=b653bf3e070940e3fc3715a2e87ee7db&language=it-IT&query=' + str)
      .then(response => {
        console.log(response);
        this.arrMovies = response.data.results;
      })
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=b653bf3e070940e3fc3715a2e87ee7db&language=it-IT&query=' + str)
      .then(response => {
        console.log(response);
        this.arrSeries = response.data.results;
      }) */
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
