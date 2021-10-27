<template>
  <div id="app">
    <FileTree :item="files"/>
  </div>
</template>

<script>
import FileTree from './components/FileTree/FileTree.vue'
import files from '../public/static/node_modules.json';

export default {
  name: 'App',
  data: () => ({
    files,
  }),
  components: {
    FileTree,
  }
}
</script>

<style>
</style>
