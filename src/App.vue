<template lang="html">

</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      films: []
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
