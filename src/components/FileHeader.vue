<template>
  <header>

    <div class="container-fluid">
      <div class="py-2 d-flex">
        <a href="#" class="me-auto">Boolflix</a>
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

<style lang="scss" scoped></style>
