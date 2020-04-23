<template lang="html">
  <div id="character-detail">
    <h3>{{character.name}}</h3>
    <img v-bind:src="character.image" alt="character image">
    <p>Species: {{character.species}}</p>
    <p>Origin:{{character.origin.name}}</p>
    <p>Location:{{character.location.name}}</p>
    <p>Number of Appearances: {{character.episode.length}}</p>
  </div>
</template>

<script>

export default {
  name: 'character-detail',
  props: ['character']
}
</script>

<style lang="css" scoped>


</style>
