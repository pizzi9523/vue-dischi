<template>
  <main>
    <div class="container-fluid">
      <Disc />
    </div>
  </main>
</template>

<script>
import Disc from "./Disc.vue";
export default {
  components: {
    Disc,
  },
};
</script>

<style lang="scss">
main {
  background-color: #1e2d3b;
}
</style>