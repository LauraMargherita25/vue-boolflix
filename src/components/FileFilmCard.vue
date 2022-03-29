<template>
  <div class="col-3 gy-5">
    <div class="film_card p-2">
      <p>Titolo: {{ objMovie.title }}</p>
      <p>Titolo originale: {{ objMovie.original_title }}</p>
      <p>Lingua originale: {{ objMovie.original_language }}</p>
      <p>Voto: {{ objMovie.vote_average }}</p>
    </div>
  </div>
</template>

<script>
export default {
    name: "FileFilmCard",
    props: {
      objMovie: Object
    }
}
</script>

<style lang="scss" scoped>
.film_card{
  height: 400px;
  background-color: red;
}
</style>