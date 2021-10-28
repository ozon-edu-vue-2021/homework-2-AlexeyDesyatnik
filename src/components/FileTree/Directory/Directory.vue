<template>
  <div>
    <p v-on:click="toggleExpanded" :class="dirClasses">
      {{ item.name }}
      <span v-if="expanded">[-]</span>
      <span v-else>[+]</span>
    </p>
    <ul v-if="expanded">
      <li v-for="it in item.contents" :key="it.name">
        <Directory v-if="it.type === 'directory'" :item="it" />
        <File v-else :item="it" />
      </li>
    </ul>
  </div>
</template>

<script>
import File from '../File/File.vue';
export default {
  name: "Directory",
  props: {
    item: Object,
  },
  components: {
    File,
  },
  data: () => ({
    expanded: false,
  }),
  methods: {
    toggleExpanded() {
      this.expanded = !this.expanded;
    },
  },
  computed: {
    dirClasses() {
      return ['dir'];
    }
  }
};
</script>

<style scoped>
.dir::before {
  content: "DIR: "
}
</style>
