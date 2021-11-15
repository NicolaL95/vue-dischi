<template>
  <div class="row justify-content-center">
    <div class="song_container" v-for="song in songs" :key="song.genre">
      <img :src="song.poster" alt="" />
      <p class="title_song">{{ song.title }}</p>
      <div class="desc_song">
        <p class="author_song mb-0">{{ song.author }}</p>
        <p class="year_song">{{ song.year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      songs: [],
      API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
    };
  },
  mounted() {
    axios.get(this.API_URL).then((r) => {
      console.log(r.data);
      this.songs = r.data.response;
    });
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
