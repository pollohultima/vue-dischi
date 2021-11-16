<template>
  <main>
    <div class="container-fluid gx-4 position-relative">
      <AlbumCard />
    </div>
  </main>
</template>

<script>
import AlbumCard from "./AlbumCard.vue";

export default {
  components: {
    AlbumCard,
  },
};
</script>

<style lang="scss">
main {
  padding: 110px 0;

  .filter {
    width: 200px;
    top: -50px;
  }
}
</style>