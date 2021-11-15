<template>
  <main>
    <div class="container-fluid gx-4">
      <div class="row gx-5 gy-3 justify-content-center">
        <div class="col-2" v-for="album in albums" :key="album.title">
          <div class="card border-0 p-4">
            <img :src="album.poster" alt="" class="mb-4" />
            <h4 class="text-center text-white">
              {{ album.title.toUpperCase() }}
            </h4>
            <p class="text-center text-muted m-0">{{ album.author }}</p>
            <p class="text-center text-muted m-0">{{ album.year }}</p>
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
main {
  padding: 110px 0;
  background: #1e2d3b;
  .card {
    height: 100%;
    background-color: #2e3a46;
  }
  img {
    width: 100%;
  }
}
</style>