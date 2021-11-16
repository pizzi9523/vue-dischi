<template>
  <div class="filterBox p-4">
    <label class="text-light me-4" for="selectAuthor">Autore:</label>
    <select
      v-model="authorSelected"
      id="selectAuthor"
      @change="$emit('filter-author', authorSelected)"
    >
      <option value="">All</option>
      <option v-for="genre in autori" :key="genre" :value="genre">
        {{ genre }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      authorSelected: "",
    };
  },
  props: {
    dischi: Array,
  },

  computed: {
    autori() {
      // console.log(this.dischi);
      const allAuthor = [];

      this.dischi.forEach((disco) => {
        //console.log(disco.genre);
        if (!allAuthor.includes(disco.author)) {
          allAuthor.push(disco.author);
        }
      });
      console.log(allAuthor);
      return allAuthor;
    },
  },
};
</script>

<style>
</style>