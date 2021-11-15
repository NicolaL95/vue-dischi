<template>
  <div id="main_container">
    <SpotifyList></SpotifyList>
  </div>
</template>

<script>
import SpotifyList from "./SpotifyList";

export default {
  components: {
    SpotifyList,
  },
};
</script>

<style scoped lang="scss">
#main_container {
  background-color: #1e2d3b;
}
</style>