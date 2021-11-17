<template>
  <div>
    <GenreSelector @changeGen="pickGen" :genres="getGenre" />
    <ArtistSelector @changeArtist="pickArtist" :artists="getArtist" />

    <div v-if="!loading">
      <div
        v-if="filterItems.length != 0"
        class="row gx-5 gy-4 justify-content-center"
      >
        <div v-for="album in filterItems" class="col-2" :key="album.title">
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
      <div class="text-center text-white" v-else>
        <h2>Nothing to visualize :/</h2>
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
import ArtistSelector from "./ArtistSelector.vue";

export default {
  components: {
    GenreSelector,
    ArtistSelector,
  },

  data() {
    return {
      albums: [],
      loading: true,
      genre: "default",
      artist: "default",
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

    pickGen(genre) {
      this.genre = genre;
    },

    pickArtist(artist) {
      this.artist = artist;
    },
  },

  computed: {
    getGenre() {
      let genres = [];
      this.albums.forEach((album) => {
        if (!genres.includes(album.genre)) {
          genres.push(album.genre);
        }
      });
      console.log(genres);
      return genres;
    },

    getArtist() {
      let artists = [];
      this.albums.forEach((album) => {
        if (!artists.includes(album.author)) {
          artists.push(album.author);
        }
      });
      console.log(artists);
      return artists;
    },

    filterItems() {
      if (this.genre === "default" && this.artist === "default") {
        return this.albums;
      } else if (this.genre !== "default" && this.artist !== "default") {
        return this.albums.filter(
          (album) => album.genre === this.genre && album.author === this.artist
        );
      }

      return this.albums.filter(
        (album) => album.genre === this.genre || album.author === this.artist
      );
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