<template lang="html">

<div>
  <ul>
    <list-character v-for="(character, index) in characters" :character="character"></list-character>
  </ul>
</div>

</template>

<script>
import ListCharacter from './ListCharacter.vue'

export default {
  name: 'character-list',
  props: ['characters'],
  components: {
    'list-character': ListCharacter
  }
}
</script>

<style lang="css" scoped>
</style>
