<template>
  <Directory 
    v-if="item.type === 'directory'"
    :item="item"
    fullPath="/"
  />
  <File 
    v-else
    :item="item"
    fullPath="/"
  />
</template>

<script>
import Directory from './Directory/Directory.vue';
import File from './File/File.vue';

export default {
  name: 'FileTree',
  props: {
    item: Object,
  },
  components: {
    Directory,
    File,
  }
}
</script>

<style scoped>

</style>
