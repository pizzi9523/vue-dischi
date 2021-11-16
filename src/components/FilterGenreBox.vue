<template>
  <div class="filterBox p-4">
    <label class="text-light me-4" for="selectGenre">Genere:</label>
    <select
      v-model="genreSelected"
      id="selectGenre"
      @change="$emit('filter-genre', genreSelected)"
    >
      <option selected value="All">All</option>
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      genreSelected: "",
    };
  },
};
</script>

<style>
</style>