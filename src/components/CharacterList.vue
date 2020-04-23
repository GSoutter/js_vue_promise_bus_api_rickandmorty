<template lang="html">

<div>
  <ul>
    <list-character v-for="(character, index) in characters" :character="character"></list-character>
  </ul>
  <!-- <select v-model="characterSelect" v-on:change="handleSelect">
    <list-character-select v-for="(character, index) in characters" :character="character"></list-character-select>
  </select> -->
</div>

</template>

<script>
import ListCharacter from './ListCharacter.vue'
import ListCharacterSelect from './ListCharacterSelect.vue'
import {eventBus} from "../main.js"


export default {
  name: 'character-list',
  data(){
    return {
      characterSelect: null
    }
  },
  props: ['characters'],
  components: {
    'list-character': ListCharacter,
    'list-character-select': ListCharacterSelect
  },
  methods: {
    handleSelect(){
      // console.log('click', this.character);
      eventBus.$emit('character-selected', this.characterSelect)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
