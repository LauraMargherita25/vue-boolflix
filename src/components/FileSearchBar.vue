<template>
  <div class="d-flex align-items-center">
    <input
      class="form-control me-2"
      type="search"
      placeholder="Search"
      v-model="serchInput"
    />
    <button 
      class="btn btn-danger" 
      type="submit"
      @click="$emit('search', serchInput)"
      >Search</button>
  </div>
</template>

<script>
export default {
  name: "FileSearchBar",
  data() {
    return {
      serchInput: "",
    }
  }
};
</script>

<style lang="scss" scoped>

</style>
