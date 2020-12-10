<template>
  <div id="app">
    <Comments/>
  </div>
</template>

<script>

import Comments from './components/Comments';
export default {
  name: 'App',
  components: {
    Comments
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin:0;
  padding:0;
  box-sizing: border-box;
  font-size: 16px;
}
</style>
