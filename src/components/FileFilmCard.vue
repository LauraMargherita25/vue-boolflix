<template>
  <div class="col-3 gy-5">
    <div
    class="film_card p-2 bg-danger" 
    :style="{
      'background-image': `url(https://image.tmdb.org/t/p/w342${objCard.img})`,
      'background-size': 'cover',
      'background-position': 'center',
      'background-repeat': 'no-repeat',
      }">
      <p>Titolo: {{ objCard.title }}</p>
      <p>Titolo originale: {{ objCard.originalTitle }}</p>
      <p>Lingua originale: <lang-flag :iso="objCard.lang" :squared="false" /></p>
      <p>Voto: {{ getRating() }}</p>
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
    },
    methods:{
      getRating() {
        return Math.ceil(this.objCard.rating / 2) 
      }
    }
}
</script>

<style lang="scss" scoped>
.film_card{
  height: 400px;
}
</style>