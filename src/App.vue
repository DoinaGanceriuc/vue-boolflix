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
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

</style>
