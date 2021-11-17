<template>
  <select
    class="form-select filterGen position-absolute"
    aria-label="Default select example"
    v-model="selector"
    @change="$emit('changeGen', selector)"
  >
    <option value="default">Select a Genre</option>
    <option v-for="genre in genres" :value="genre" :key="genre">
      {{ genre }}
    </option>
  </select>
</template>

<script>
export default {
  props: {
    genres: Array,
  },

  data() {
    return {
      selector: "default",
    };
  },
};
</script>

<style lang="scss">
.filterGen {
  width: 200px !important;
  top: -50px;
}
</style>