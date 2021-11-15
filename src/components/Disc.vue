<template>
  <div class="row justify-content-center p-3 text-center">
    <div class="col-md-2 my-4" v-for="disc in discs" :key="disc.title">
      <div class="disc">
        <img class="p-4" :src="disc.poster" alt="" />
        <h2 class="disc_title text-light fs-2">
          {{ disc.title.toUpperCase() }}
        </h2>
        <div class="disc_author fs-4">{{ disc.author }}</div>
        <div class="disc_year fs-4">{{ disc.year }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      discs: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        console.log(response.data.response);
        this.discs = response.data.response;
        console.log(this.discs);
      })
      .catch((error) => {
        console.log(error, "ERRORE");
      });
  },
};
</script>

<style lang="scss">
.disc {
  height: 100%;
  margin: 10px;
  background-color: #2e3a46;
  img {
    width: 100%;
  }
  .disc_title,
  .disc_author,
  .disc_year {
    color: #758080;
  }
}
</style>