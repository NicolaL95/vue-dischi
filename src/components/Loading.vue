<template>
  <div class="loading">
    <h1>CARICAMENTO IN CORSO</h1>
  </div>
</template>

<script>
export default {};
</script>

<style scoped lang="scss">
.loading {
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  height: calc(100vh - 70px);
  h1 {
    font-size: 4rem;
  }
}
</style>