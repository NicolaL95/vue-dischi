<template>
  <div class="row justify-content-center" v-if="loading">
    <Select @find="findGenre" @findA="findArtist" />
    <div class="song_container" v-for="song in filterSong" :key="song.author">
      <img :src="song.poster" alt="" />
      <p class="title_song">{{ song.title }}</p>
      <div class="desc_song">
        <p class="author_song mb-0">{{ song.author }}</p>
        <p class="year_song">{{ song.year }}</p>
      </div>
    </div>
  </div>
  <div v-else>
    <Loading></Loading>
  </div>
</template>

<script>
import axios from "axios";
import Loading from "./Loading.vue";
import Select from "./Select";

export default {
  components: {
    Loading,
    Select,
  },
  methods: {
    findGenre(selGen) {
      this.filGenre = selGen;
      this.filtedArray = this.songs;
    },
    findArtist(selArt) {
      this.filArtist = selArt;
      this.filtedArray = this.songs;
    },
  },
  data() {
    return {
      songs: [],
      loading: false,
      filGenre: "All",
      filArtist: "All",
      filtedArray: "",
      API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
    };
  },
  mounted() {
    axios.get(this.API_URL).then((r) => {
      this.songs = r.data.response;
      this.loading = r.data.success;
    });
  },
  computed: {
    /*  filterSong() {
      if (this.filGenre == "All" || this.filGenre == "") {
        return this.songs;
      }
      const filtered = this.songs.filter((songList) => {
        return songList.genre.includes(this.filGenre);
      });
      return filtered;
    }, */
    /*   filterSong() {
      if (this.filArtist == "All" || this.filArtist == "") {
        return this.songs;
      }
      const filtered = this.songs.filter((songList) => {
        return songList.author.includes(this.filArtist);
      });
      return filtered;
    }, */
    filterSong() {
      if (this.filArtist == "All") {
        if (this.filGenre == "All") {
          console.log("All-All");
          return this.songs;
        } else {
          console.log("?-All");
          const filtered = this.songs.filter((songList) => {
            return songList.genre.includes(this.filGenre);
          });
          return filtered;
        }
      } else if (this.filGenre == "All") {
        if (this.filArtist == "All") {
          console.log("All-All");
          return this.songs;
        } else {
          console.log("All-?");
          const filtered = this.songs.filter((songList) => {
            return songList.author.includes(this.filArtist);
          });
          return filtered;
        }
      }
      console.log("?-?");
      const filtered = this.songs.filter((songList) => {
        return (
          songList.author.includes(this.filArtist) &&
          songList.genre.includes(this.filGenre)
        );
      });
      return filtered;
    },
  },
};
</script>

<style lang="scss" scoped>
.row {
  margin-top: 20px;
  width: 100%;
  .song_container {
    margin: 20px;
    background-color: #2e3a46;
    width: auto;
    img {
      width: 230px;
      margin: 10px 0;
    }
    .title_song {
      color: white;
      text-align: center;
      width: 230px;
      text-transform: uppercase;
      font-size: 1.3rem;
      font-weight: bold;
    }
    .desc_song {
      color: #78746a;
      text-align: center;
      font-weight: bold;
    }
  }
}
</style>
