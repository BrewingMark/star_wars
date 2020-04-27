<template lang="html">
  <div>
    <h1>Characters</h1>
    <film-filter-form :films="films" />
    <film-detail v-if="selectedFilm" :film="selectedFilm"/>
  </div>
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      films: [],
      selectedFilm: null
    }
  },
  mounted(){
    fetch('https://swapi.dev/api/films/')
    .then(res => res.json())
    .then(data => this.films = data.results)
  }
}
</script>

<style lang="css" scoped>
</style>
