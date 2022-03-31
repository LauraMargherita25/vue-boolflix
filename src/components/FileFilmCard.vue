<template>
  <div class="col-3 gy-5">
    <div
    class="film_card p-2" 
    :style="{
      'background-image': `url(https://image.tmdb.org/t/p/w342${objCard.img})`,
      'background-size': 'cover',
      'background-position': 'center',
      'background-repeat': 'no-repeat',
      }">
      <div class="info_wrapper">
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
.film_card{
  height: 400px;
  background-color: red;
  .info_wrapper{
    display: none;
  }
  &:hover {
    background-color: aqua;

    animation: flip-in-ver-right 1s cubic-bezier(0.250, 0.460, 0.450, 0.940) both;
    .info_wrapper{
      display: block;
    }
  }


}
@keyframes flip-in-ver-right {
  0% {
    transform: rotateY(-180deg);
    opacity: 0;
  }
  100% {
    transform: rotateY(0);
    opacity: 1;
  }

  // .info_wrapper{
  //     display: none;
  //   }
  // &:hover{
  //   background-color: aqua;
  //   cursor: pointer;
  //   animation: rotate 3s;
  //   .info_wrapper{
  //     display: block;
  //   }
  // }
  // @keyframes rotate{
  //   0%   {transform: rotateY(0deg);}
  //   100% {transform: rotateY(180deg);}
  // }
}
</style>