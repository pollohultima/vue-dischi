<template>
  <div>
    <GenreSelector @changeGen="pickGen" />
    <div class="row gx-5 gy-4 justify-content-center" v-if="!loading">
      <div class="col-2" v-for="album in genFilter" :key="album.title">
        <div class="card border-0 p-4">
          <img :src="album.poster" alt="" class="mb-4" />
          <h5 class="text-center text-white">
            {{ album.title.toUpperCase() }}
          </h5>
          <p class="text-center text-muted m-0">{{ album.author }}</p>
          <p class="text-center text-muted m-0">{{ album.year }}</p>
        </div>
      </div>
    </div>
    <div v-else>
      <h2 class="text-center text-white">Loading...</h2>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import GenreSelector from "./GenreSelector.vue";

export default {
  components: {
    GenreSelector,
  },

  data() {
    return {
      albums: [],
      loading: true,
      selectItem: "default",
    };
  },

  mounted() {
    setTimeout(this.callAPI, 2000);
  },

  methods: {
    callAPI() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((r) => {
          this.albums = r.data.response;
          this.loading = false;
        })
        .catch((error) => {
          console.log(error, "ERROR");
        });
    },

    pickGen(selectedGen) {
      this.selectItem = selectedGen;
    },
  },

  computed: {
    genFilter() {
      if (this.selectItem === "default") {
        return this.albums;
      } else {
        const filteredItem = this.albums.filter((album) => {
          return album.genre.includes(this.selectItem);
        });
        return filteredItem;
      }
    },
  },
};
</script>

<style lang="scss">
.card {
  height: 100%;
  background-color: #2e3a46 !important;
}
img {
  width: 100%;
}
</style>