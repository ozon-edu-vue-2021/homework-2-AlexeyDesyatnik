<template>
  <p>{{ contents.name }}</p>
</template>

<script>
export default {
  name: "Directory",
  props: {
    contents: Object,
  },
};
</script>

<style scoped>
</style>
