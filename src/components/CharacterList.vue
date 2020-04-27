<template lang="html">
  <div v-if="characters" class="character-list">
    <h3>character List</h3>
    <ul>
      <character-list-item v-for="(character, index) in characters" :key="index" :character="character"></Character-list-item >
    </ul>
  </div>
</template>

<script>

import CharacterListItem from './CharacterListItem.vue'

export default {
  name: 'character-list',
  props: ['characters'],
  components: {
    'character-list-item': CharacterListItem
  }
}
</script>

<style lang="css" scoped>
</style>
