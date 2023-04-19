<template>
  <div id="app">
    <my-root :folder="root" />
  </div>
</template>

<script>
import MyRoot from './components/Root.vue'
export default {
  name: 'App',
  components: { MyRoot },
  data() {
    return {
      root: {
        text: 'Root Folder',
        leaf: false,
        expanded: true,
        children: [{
          text: 'Sub Folder 1',
          leaf: false,
          expanded: false,
          children: [{
            text: 'Sub Sub Folder 1',
            leaf: false,
            expanded: false,
            children: [{
              text: 'SomeFile1.js',
              leaf: true
            }]
          }, {
            text: 'Sub Sub Folder 2',
            leaf: false,
            expanded: false,
            children: []
          }, {
            text: 'SomeFile.txt',
            leaf: true
          }]
        }]
      }
    }
  }
}
</script>

<style></style>
