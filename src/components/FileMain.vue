<template>
  <main>
    <div class="container">
      <div class="row">
        <file-film-card v-for="movie in arrMovies" :key="movie.title" :objMovie="movie"/>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios';
import FileFilmCard from "./FileFilmCard.vue"
export default {
    name: "FileMain",

    components: {
      FileFilmCard
    },

    data(){
      return {
        arrMovies: []
      }
    },

    props: {
      searchData: String,
    },

    created() {
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=+searchData') 
        .then((response) => {
          this.arrMovies = response.data.results;
    })
  }
}
</script>

<style lang="scss" scoped></style>
