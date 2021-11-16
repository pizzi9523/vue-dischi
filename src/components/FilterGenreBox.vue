<template>
  <div class="filterBox p-4">
    <label class="text-light me-4" for="selectGenre">Genere:</label>
    <select
      v-model="genreSelected"
      id="selectGenre"
      @change="$emit('filter-genre', genreSelected)"
    >
      <option value="">All</option>
      <option v-for="genre in generi" :key="genre" :value="genre">
        {{ genre }}
      </option>
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

  props: {
    dischi: Array,
  },

  computed: {
    generi() {
      // console.log(this.dischi);
      const allGenre = [];

      this.dischi.forEach((disco) => {
        //console.log(disco.genre);
        if (!allGenre.includes(disco.genre)) {
          allGenre.push(disco.genre);
        }
      });
      console.log(allGenre);
      return allGenre;
    },
  },
};
</script>

<style>
</style>