<template>
  <main>
    <div class="container">
      <div class="row" v-show="arrMovies.length !== 0">
        <h2 class="text-light">Film</h2>
        <file-film-card v-for="movie in arrMovies" :key="movie.title" :objCard="movie"/>
      </div>
      <div class="row mt-5" v-show="arrSeries.length !== 0">
        <h2 class="text-light">Serie tv</h2>
        <file-film-card v-for="serie in arrSeries" :key="serie.title" :objCard="serie"/>
      </div>
    </div>
  </main>
</template>

<script>
import FileFilmCard from "./FileFilmCard.vue"
export default {
    name: "FileMain",

    components: {
      FileFilmCard
    },

    props: {
      searchData: String,
      arrMovies: Array,
      arrSeries: Array,
    },

}
</script>

<style lang="scss" scoped></style>
