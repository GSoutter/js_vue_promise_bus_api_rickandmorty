<template lang="html">
  <div>
    <h1>Rick and Morty Charater List</h1>
    <character-list :characters='characters'></character-list>
  </div>
</template>

<script>
import CharacterList from './components/CharacterList.vue'
import {eventBus} from "./main.js"

export default {
  name: 'app',
  data(){
    return {
      characters: [],
      selectedCharacter: null
    }
  },
  mounted(){

    fetch('https://rickandmortyapi.com/api/character/')
    .then(res => res.json())
    .then(characters => this.characters = characters.results)

    eventBus.$on('character-selected', (character)=> {
      this.selectedCharacter = character;
    })
  },
  components: {
    'character-list': CharacterList,

  }
}
</script>

<style lang="css" scoped>
</style>
