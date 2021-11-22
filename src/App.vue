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
@import './assets/scss/variables.scss';
@import './assets/scss/common.scss';
</style>
