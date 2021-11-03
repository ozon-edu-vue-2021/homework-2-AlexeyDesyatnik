<template>
  <div>
    <div class="selected-file-panel">Selected file: {{ selectedFilePath }}</div>
    <div class="file-tree">
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
.selected-file-panel {
  border-bottom: 1px solid black;
  position: sticky;
  top: 0px;
  background: white;
}
.file-tree {
  margin-top: 30px;
}
</style>
