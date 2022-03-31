<template>
  <div class="col-3 gy-5">
    <div class="item_card">
      <div class="item_card-wrapper">
        <div class="card-front">
          <img :src="'https://image.tmdb.org/t/p/w342' + objCard.img" alt="Avatar" style="width:100%;height:100%;">
        </div>
        <div class="card-back">
          <div class="p-2">
            <p>Titolo: {{ objCard.title }}</p>
            <p>Titolo originale: {{ objCard.originalTitle }}</p>
            <p>Lingua originale: <lang-flag :iso="objCard.lang" :squared="false" /></p>
            <ul class="d-flex align-items-baseline p-0">
              <p>Voto:</p>
              <li v-for="star in getRating(objCard.rating)" :key="star" class="text-warning p-1"><i class="fa-solid fa-star"></i></li>
            </ul>
          </div>
        </div>
      </div>
    </div> 
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: "FileFilmCard",
  components: {
    LangFlag,
  },
  props: {
    objCard: Object
  },
  methods:{
    getRating(x) {
      return Math.ceil(x / 2);
    },
  },
}
</script>

<style lang="scss" scoped>
.item_card {
  background-color: transparent;
  width: 300px;
  height: 400px;
  perspective: 1000px; 
  .item_card-wrapper {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.8s;
    transform-style: preserve-3d;
    .card-front, .card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
    }
    .card-back {
      background-color: red;
      color: white;
      transform: rotateY(180deg);
    }
  }
  &:hover .item_card-wrapper {
    transform: rotateY(180deg);
  }
}
</style>