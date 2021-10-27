<template>
  <p>LINK: {{ item.name }}</p>
</template>

<script>
export default {
  name: "Link",
  props: {
    item: Object,
  },
};
</script>

<style scoped>
</style>
