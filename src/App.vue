<template lang="html">
  <div>
    <h1>Characters</h1>
    <film-filter-form :films="films" />
    <film-detail v-if="selectedFilm" :film="selectedFilm"/>
  </div>
</template>

<script>

import FilmFilterForm from './components/FilmFilterForm.vue'
import FilmDetail from './components/FilmDetail.vue'
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return {
      films: [],
      selectedFilm: null
    }
  },
  components: {
    "film-filter-form": FilmFilterForm,
    "film-detail": FilmDetail
  },
  mounted(){
    fetch('https://swapi.dev/api/films/')
    .then(res => res.json())
    .then(data => this.films = data.results)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })
  }
}
</script>

<style lang="css" scoped>
</style>
