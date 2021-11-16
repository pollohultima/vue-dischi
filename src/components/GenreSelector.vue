<template>
  <select
    class="form-select filter position-absolute"
    aria-label="Default select example"
    v-model="selector"
    @change="$emit('changeGen', selector)"
  >
    <option value="default">Select a Genre</option>
    <option value="Rock">Rock</option>
    <option value="Pop">Pop</option>
    <option value="Jazz">Jazz</option>
    <option value="Metal">Metal</option>
  </select>
</template>

<script>
export default {
  data() {
    return {
      selector: "default",
    };
  },
};
</script>

<style lang="scss">
.filter {
  width: 200px;
  top: -50px;
}
</style>