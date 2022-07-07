<template>
  <div id="app">
    <randomcat></randomcat>
  </div>
</template>

<script>

import randomcat from '@/components/randomcat.vue'
export default {
  name: 'App',
  components: {
    randomcat
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;

}

body {
  margin:0px;
}
</style>
