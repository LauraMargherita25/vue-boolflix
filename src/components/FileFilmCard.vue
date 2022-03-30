<template>
  <div class="col-3 gy-5">
    <div
    class="film_card p-2 bg-danger text-light" 
    :style="{
      'background-image': `url(https://image.tmdb.org/t/p/w342${objCard.img})`,
      'background-size': 'cover',
      'background-position': 'center',
      'background-repeat': 'no-repeat',
      'filter': 'brightness(.5)',
      }">
      <p>Titolo: {{ objCard.title }}</p>
      <p>Titolo originale: {{ objCard.original_title }}</p>
      <p>Lingua originale: <lang-flag :iso="objCard.lang" :squared="false" /></p>
      <p>Voto: {{ objCard.vote_average }}</p>
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
      objCard: Object
    }
}
</script>

<style lang="scss" scoped>
.film_card{
  height: 400px;
}
</style>