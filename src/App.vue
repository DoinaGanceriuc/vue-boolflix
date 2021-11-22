<template>
  <div id="app">
    <Movies/>
  </div>
</template>

<script>
import Movies from './components/Movies.vue'

export default {
  name: 'App',
  components: {
    Movies
  }
}
</script>

<style lang="scss">
@import '../node_modules/@fortawesome/fontawesome-free/css/all.css';
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: #434343;
}
.container {
  max-width: 1200px;
  margin: auto;
}

</style>
