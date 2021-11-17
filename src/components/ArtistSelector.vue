<template>
  <select
    class="form-select filterArt position-absolute"
    aria-label="Default select example"
    v-model="selectorArt"
    @change="$emit('changeArtist', selectorArt)"
  >
    <option value="default">Select an Artist</option>
    <option v-for="artist in artists" :value="artist" :key="artist">
      {{ artist }}
    </option>
  </select>
</template>

<script>
export default {
  props: {
    artists: Array,
  },

  data() {
    return {
      selectorArt: "default",
    };
  },
};
</script>

<style lang="scss">
.filterArt {
  width: 200px !important;
  top: -50px;
  left: 250px;
}
</style>