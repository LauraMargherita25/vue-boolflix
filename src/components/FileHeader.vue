<template>
  <header class="bg-secondary mb-5">

    <div class="container-fluid">
      <div class="py-2 d-flex">
        <a href="#" class="me-auto">
          <p class="h1 fw-bold text-uppercase text-danger">Boolflix</p>
        </a>
        <file-search-bar @search="searchString($event)"/>
      </div>
    </div>

  </header>
</template>

<script>
import FileSearchBar from "./FileSearchBar.vue";

export default {
  name: "FileHeader",

  components: {
    FileSearchBar,
  },

  methods: {
    searchString(strToSearch) {
      this.$emit('search', strToSearch)
    }
  }
};
</script>

<style lang="scss" scoped>

</style>
