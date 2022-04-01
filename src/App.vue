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

      const objParams = {
        api_key: this.apiKey,
        lang: 'it-IT',
        query: str,
      }

      if (str == "") {
        return
      }
      // ricerca film
      this.axiosCall('movie', objParams)

      // ricerca serie
      this.axiosCall('tv', objParams)

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
    },
    axiosCall(searchType, objParams) {  

      axios.get(this.apiUrl + 'search/' + searchType, {
        params: objParams
      })
      .then(response => {
        if (searchType === 'movie'){
          this.arrMovies = response.data.results.map((movie) => ({
            id: movie.id,
            title: movie.title,
            originalTitle: movie.original_title,
            lang: movie.original_language,
            rating: movie.vote_average,
            img: movie.poster_path,
            trama: movie.overview,
          }));
        } else if (searchType === 'tv') {
          this.arrSeries = response.data.results.map((serie) => ({
            id: serie.id,
            title: serie.name,
            originalTitle: serie.original_name,
            lang: serie.original_language,
            rating: serie.vote_average,
            img: serie.poster_path,
            trama: serie.overview,
          }));
        }
      })
    },
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
