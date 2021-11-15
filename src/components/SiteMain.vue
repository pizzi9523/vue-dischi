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
  min-height: 100vh;
  background-color: #1e2d3b;
}
</style>