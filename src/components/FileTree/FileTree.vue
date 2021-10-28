<template>
  <div>
    <div>Selected file: {{ selectedFilePath }}</div>
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
  </div>
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
  },
  data: () => ({
    selectedFilePath: null,
  }),
  methods: {
    onFileSelected(selectedFilePath) {
      this.selectedFilePath = selectedFilePath;
    }
  },
  created() {
    this.$root.$on('fileSelected', this.onFileSelected);
  },
  beforeDestroy() {
    this.$root.$off('fileSelected', this.onFileSelected);
  }
}
</script>

<style scoped>

</style>
