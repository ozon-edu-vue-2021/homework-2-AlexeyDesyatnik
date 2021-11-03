<template>
  <p v-on:click="selectFile" :class="fileClasses">
    {{ item.name }}
  </p>
</template>

<script>
export default {
  name: "File",
  props: {
    item: Object,
    fullPath: String
  },
  data: () => ({
    selectedFilePath: null,
  }),
  methods: {
    selectFile() {
      if (this.isSelected) {
        this.$root.$emit('fileSelected', null);
      } else {
        this.$root.$emit('fileSelected', this.path);
      }
    },
    onFileSelected(selectedFilePath) {
      this.selectedFilePath = selectedFilePath;
    }
  },
  computed: {
    path() {
      return this.fullPath + this.item.name;
    },
    isSelected() {
      return this.selectedFilePath === this.path;
    },
    fileClasses() {
      return [
        'file', {
          'file_isLink': this.item.type === 'link',
          'file_selected': this.isSelected,
        },
      ];
    },
  },
  created() {
    this.$root.$on('fileSelected', this.onFileSelected);
  },
  beforeDestroy() {
    this.$root.$off('fileSelected', this.onFileSelected);
  }
};
</script>

<style scoped>
.file::before {
  content: 'FILE: ';
}

.file:hover {
  cursor: pointer;
}

.file_isLink::before {
  content: 'LINK: ';
}

.file_selected {
  background: #d0d0d0;
}
</style>
