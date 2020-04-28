<template lang="html">
  <div v-if="film">
    <div>
      <h2>Episode {{film.episode_id}}: {{film.title}}</h2>
      <p>Director: {{film.director}}</p>
      <p>Release date: {{film.release_date}}</p>
    </div>

    <div>
      <character-list v-if="film.length" :characters="characters"></character-list>
    </div>

  </div>
</template>

<script>

import CharacterList from './CharacterList.vue'

export default {
  name: 'film-detail',
  props: ['film'],
  components: {
    'character-list': CharacterList
  },
  data() {
    return {
      characters: []
    }
  },
  methods: {
    getCharacters(){
      const filmPromises = this.film.characters.map((characterUrl) => {
        return fetch(characterUrl).then(response => response.json())
      })
      Promise.all(filmPromises)
      .then(data => this.characters = data);
    }
  },
  mounted(){
    this.getCharacters();
  },
  watch: {
    film: function(){
      this.getCharacters();
    }
  }
}
</script>

<style lang="css" scoped>
</style>
