<template>
  <div id="app">
    <directory :contents="files"/>
  </div>
</template>

<script>
import Directory from './components/Directory/Directory.vue'
import files from '../public/static/node_modules.json';

export default {
  name: 'App',
  data: () => ({
    files,
  }),
  components: {
    Directory
  }
}
</script>

<style>
</style>
