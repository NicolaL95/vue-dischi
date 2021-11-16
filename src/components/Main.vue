<template>
  <div id="main_container">
    <Select @find="findGenre" />
    <SpotifyList></SpotifyList>
  </div>
</template>

<script>
import SpotifyList from "./SpotifyList";
import Select from "./Select";

export default {
  components: {
    SpotifyList,
    Select,
  },
  methods: {
    findGenre() {
      console.log("9");
    },
  },
};
</script>

<style scoped lang="scss">
</style>