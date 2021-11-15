<template>
  <main>
    <div class="container-fluid">
      <div class="row">
        <div class="col-2" v-for="album in albums" :key="album.title">
          <div class="card">
            <img :src="album.poster" alt="" />
            <h6>{{ album.title }}</h6>
            <p>{{ album.author }}</p>
            <p>{{ album.year }}</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      albums: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((r) => {
        this.albums = r.data.response;
      });
  },
};
</script>

<style lang="scss">
.card {
}
</style>