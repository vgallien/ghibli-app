<template>
  <div id="app">
    <movie-list></movie-list>
  </div>
</template>

<script>

import MovieList from './components/MovieList'

export default {
  name: 'App',
  components: {
      'movie-list': MovieList
  }
}
</script>

<style>

</style>
