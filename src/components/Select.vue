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
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>

    <select
      name="fil_art"
      v-model="selectArtist"
      placeholder="All"
      id="fil_art"
      @change="$emit('findA', selectArtist)"
    >
      <option value="All">All</option>
      <option value="Bon Jovi">Bon Jovi</option>
      <option value="Queen">Queen</option>
      <option value="Steve Gadd Band">Steve Gadd Band</option>
      <option value="Iron Maiden">Iron Maiden</option>
      <option value="Eric Clapton">Eric Clapton</option>
      <option value="Deep Purple">Deep Purple</option>
      <option value="Metallica">Metallica</option>
      <option value="Dave Weckl">Dave Weckl</option>
      <option value="Michael Jacjson">Michael Jacjson</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectGenre: "All",
      selectArtist: "All",
    };
  },
};
</script>

<style>
.selector {
  margin-left: 10px;
}
</style>