<template>
  <div class="filterBox p-4">
    <label class="text-light me-4" for="selectGenre">Genere:</label>
    <select
      v-model="genreSelected"
      id="selectGenre"
      @change="$emit('filter-genre', genreSelected)"
    >
      <option value="">test</option>
      <option value="">All</option>
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
    <button class="p-5" @click="generi">TEST</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      genreSelected: "",
      allGenre: [],
    };
  },

  props: {
    dischi: Array,
  },

  methods: {
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