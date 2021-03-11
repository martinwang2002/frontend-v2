<template>
  <div class="d-flex flex-row align-start flex-breakline">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'FactTable'
}
</script>

<style scoped>
.flex-breakline {
  flex-flow: wrap;
  word-break: keep-all;
}
</style>
