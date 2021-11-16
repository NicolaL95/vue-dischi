<template>
  <div class="selector">
    <select
      name="fil_gen"
      v-model="selectGenre"
      placeholder="All"
      id="fil_gen"
      @change="$emit('find', selectGenre)"
    >
      <option value="All">All</option>
      <option v-for="song in indexGenre" :key="song" :value="song">
        {{ song }}
      </option>
    </select>

    <select
      name="fil_art"
      v-model="selectArtist"
      placeholder="All"
      id="fil_art"
      @change="$emit('findA', selectArtist)"
    >
      <option value="All">All</option>
      <option v-for="song in indexAuthor" :key="song" :value="song">
        {{ song }}
      </option>
    </select>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      selectGenre: "All",
      selectArtist: "All",
      API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
      arrayList: [],
    };
  },
  mounted() {
    axios.get(this.API_URL).then((r) => {
      this.arrayList = r.data.response;
    });
  },
  computed: {
    indexGenre() {
      let arrayPlacer = [];
      this.arrayList.forEach((element) => {
        if (arrayPlacer.includes(element.genre) == false) {
          arrayPlacer.push(element.genre);
        }
      });
      return arrayPlacer;
    },
    indexAuthor() {
      let arrayPlacer = [];
      this.arrayList.forEach((element) => {
        if (arrayPlacer.includes(element.author) == false) {
          arrayPlacer.push(element.author);
        }
      });
      return arrayPlacer;
    },
  },
};
</script>

<style>
.selector {
  margin-left: 10px;
}
</style>