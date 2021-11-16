<template>
  <div class="selector">
    <select
      name="fil_gen"
      v-model="selectValue"
      placeholder="All"
      id="fil_gen"
      @change="$emit('find', selectValue)"
    >
      <option value="All">All</option>
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectValue: "All",
    };
  },
};
</script>

<style>
.selector {
  margin-left: 10px;
}
</style>