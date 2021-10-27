<template>
  <div>
    <p>DIR: {{ item.name }}</p>
    <ul>
      <li v-for="it in item.contents" :key="it">
        <FileTree :item="it" />
      </li>
    </ul>
  </div>
</template>

<script>
import FileTree from '../FileTree.vue';

export default {
  name: "Directory",
  props: {
    item: Object,
  },
  components: {
    FileTree,
  }
};
</script>

<style scoped>
</style>
