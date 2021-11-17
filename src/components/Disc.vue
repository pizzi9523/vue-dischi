<template>
  <div>
    <FilterGenreBox @filter-genre="filterGenreSelection" :dischi="discs" />
    <FilterAuthorBox @filter-author="filterAuthorSelection" :dischi="discs" />
    <div class="row justify-content-center p-5 text-center" v-if="!loading">
      <div class="col-md-2 my-4" v-for="disc in filteredList" :key="disc.title">
        <div class="disc p-3">
          <img class="p-2" :src="disc.poster" alt="" />
          <h2 class="fs-5 disc_title text-light p-2">
            {{ disc.title.toUpperCase() }}
          </h2>
          <div class="disc_author fs-6">{{ disc.author }}</div>
          <div class="disc_year fs-6">{{ disc.year }}</div>
        </div>
      </div>
    </div>

    <div class="display-5 text-light p-5" v-else>Loading...</div>
  </div>
</template>

<script>
import axios from "axios";
import FilterGenreBox from "./FilterGenreBox.vue";
import FilterAuthorBox from "./FilterAuthorBox.vue";

export default {
  data() {
    return {
      discs: [],
      loading: true,
      selectedGenre: "",
      selectedAuthor: "",
    };
  },

  components: {
    FilterGenreBox,
    FilterAuthorBox,
  },

  mounted() {
    setTimeout(this.callApi, 1 * 1000);
  },
  methods: {
    callApi() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          //console.log(response.data.response);
          this.discs = response.data.response;
          this.loading = false;
          //console.log(this.discs);
        })
        .catch((error) => {
          console.log(error, "ERRORE");
        });
    },

    filterGenreSelection(selectedGen) {
      //console.log(selectedGen);
      this.selectedGenre = selectedGen;
    },

    filterAuthorSelection(selectedAut) {
      this.selectedAuthor = selectedAut;
    },
  },
  computed: {
    filteredList() {
      if (this.selectedGenre === "" && this.selectedAuthor === "") {
        return this.discs;
      } else {
        let fullFiltered = this.discs.filter((disc) => {
          return (
            disc.author.includes(this.selectedAuthor) &&
            disc.genre.includes(this.selectedGenre)
          );
        });
        //console.log(fullFiltered);
        return fullFiltered;
        //console.log(filteredCharacter);
      }

      /* if (this.selectedGenre === "" && this.selectedAuthor === "") {
        return this.discs;
      } else if (this.selectedGenre !== "" && this.selectedAuthor === "") {
        const filteredGenere = this.discs.filter((disc) => {
          return disc.genre.includes(this.selectedGenre);
        });
        //console.log(filteredCharacter);
        //console.log(filteredGenere);
        return filteredGenere;
      } else if (this.selectedAuthor !== "" && this.selectedGenre === "") {
        const filteredAutore = this.discs.filter((disc) => {
          return disc.author.includes(this.selectedAuthor);
        });
        return filteredAutore;
      } else if (this.selectedGenre !== "" && this.selectedAuthor !== "") {
        let fullFiltered = this.discs.filter((disc) => {
          return (
            disc.author.includes(this.selectedAuthor) &&
            disc.genre.includes(this.selectedGenre)
          );
        });
        //console.log(fullFiltered);
        return fullFiltered;

        //console.log(filteredCharacter);
      } else {
        console.log("ERROR");
        return 0;
      } */
    },
  },
};
</script>

<style lang="scss">
.disc {
  height: 100%;
  margin: 10px;
  background-color: #2e3a46;
  &:hover {
    background-color: #103d64;
    cursor: pointer;
  }
  img {
    width: 100%;
  }
  .disc_title,
  .disc_author,
  .disc_year {
    color: #758080;
  }
}

.filterBox {
  display: inline-block;
  select {
    color: black;
    border-radius: 1rem;
    padding: 5px;
  }
}
</style>