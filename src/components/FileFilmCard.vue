<template>
  <div class="col-3">
    <div class="film_card">
      <p>{{ objMovie.title }}</p>
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
  width: 200px;
  height: 300px;
  background-color: red;
}
</style>