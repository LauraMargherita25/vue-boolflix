<template>
  <main>
    <div class="container">
      <div class="row">
        <h2 class="text-light">Film</h2>
        <file-film-card v-for="movie in arrMovies" :key="movie.title" :objMovie="movie"/>
      </div>
      <div class="row">
        <h2 class="text-light">Serie tv</h2>
        <file-film-card v-for="movie in arrSeries" :key="movie.title" :objMovie="movie"/>
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
