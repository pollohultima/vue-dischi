<template>
  <main>
    <div class="container-fluid gx-4 position-relative">
      <select
        class="form-select filter position-absolute"
        aria-label="Default select example"
      >
        <option selected>Select a Genre</option>
        <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="jazz">Jazz</option>
        <option value="metal">Metal</option>
      </select>

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