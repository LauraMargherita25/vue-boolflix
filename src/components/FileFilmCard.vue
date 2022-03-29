<template>
  <div class="col-3 gy-5">
    <div class="film_card p-2 bg-danger">
      <p>Titolo: {{ objMovie.title }}</p>
      <p>Titolo originale: {{ objMovie.original_title }}</p>
      <p>Lingua originale: <lang-flag :iso="objMovie.original_language" :squared="false" /></p>
      <p>Voto: {{ objMovie.vote_average }}</p>
    </div>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: "FileFilmCard",
    components: {
      LangFlag
    },
    props: {
      objMovie: Object
    }
}
</script>

<style lang="scss" scoped>
.film_card{
  height: 400px;
}
</style>