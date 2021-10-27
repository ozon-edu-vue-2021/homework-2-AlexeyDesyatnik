<template>
  <p>FILE: {{ item.name }}</p>
</template>

<script>
export default {
  name: "File",
  props: {
    item: Object,
  },
};
</script>

<style scoped>
</style>
