<template>
  <p v-on:click="toggleSelected" :class="fileClasses">
    {{ item.name }}
  </p>
</template>

<script>
export default {
  name: "File",
  props: {
    item: Object,
    fullPath: String,
  },
  data: () => ({
    selected: false,
  }),
  methods: {
    toggleSelected() {
      this.selected = !this.selected;
    },
  },
  computed: {
    fileClasses() {
      return [
        'file', {
          'file_isLink': this.item.type === 'link',
          'file_selected': this.selected,
        },
      ];
    },
    path() {
      return this.fullPath + this.item.name;
    }
  },
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
