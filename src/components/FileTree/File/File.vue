<template>
  <p v-on:click="toggleSelected" :class="fileClasses">{{ item.name }}</p>
</template>

<script>
export default {
  name: "File",
  props: {
    item: Object,
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
  },
};
</script>

<style scoped>
.file::before {
  content: 'FILE: ';
}

.file_isLink::before {
  content: 'LINK: ';
}

.file_selected {
  background: #d0d0d0;
}
</style>
