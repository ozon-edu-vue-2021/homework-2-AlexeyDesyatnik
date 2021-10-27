<template>
  <Directory v-if="item.type === 'directory'" :item="item" />
  <File v-else-if="item.type === 'file'" :item="item" />
  <Link v-else-if="item.type === 'link'" :item="item" />
</template>

<script>
import Directory from './Directory/Directory.vue';
import File from './File/File.vue';
import Link from './Link/Link.vue';

export default {
  name: 'FileTree',
  props: {
    item: Object,
  },
  components: {
    Directory,
    File,
    Link,
  }
}
</script>

<style scoped>

</style>