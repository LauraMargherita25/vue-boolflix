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
import FileFilmCard from "./FileFilmCard.vue"
export default {
    name: "FileMain",

    components: {
      FileFilmCard
    },

    props: {
      searchData: String,
      arrMovies: Array,
    },

}
</script>

<style lang="scss" scoped></style>
