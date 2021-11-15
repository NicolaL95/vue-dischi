<template>
  <div class="container">
    <div class="row">
      <div class="song_container" v-for="song in songs" :key="song.genre">
        <img :src="song.poster" alt="" />
        <p class="title_song">{{ song.title }}</p>
        <div class="desc_song">
          <p class="author_song">{{ song.author }}</p>
          <p class="year_song">{{ song.year }}</p>
        </div>
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
</style>
