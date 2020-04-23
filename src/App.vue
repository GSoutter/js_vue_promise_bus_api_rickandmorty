<template lang="html">
  <!-- <div>
    <h1>Rick and Morty Charater List</h1>
    <character-list :characters='characters'></character-list>
    <character-detail id="character-detail" v-if="selectedCharacter" :character="selectedCharacter"></character-detail>
  </div> -->
  <div>
    <h1>Rick and Morty Character List</h1>
    <form v-on:submit.prevent="enterSearch">
        <input type="text" name="search" v-model="search">
        <button type="submit" name="button">Search</button>
    </form>
    <character-list :characters='this.filteredCharacterList'></character-list>
    <character-detail id="character-detail" v-if="selectedCharacter" :character="selectedCharacter"></character-detail>
  </div>
</template>

<script>
import CharacterList from './components/CharacterList.vue'
import {eventBus} from "./main.js"
import CharacterDetail from './components/CharacterDetail.vue'


export default {
  name: 'app',
  data(){
    return {
      characters: [],
      selectedCharacter: null,
      search: '',
      filteredCharacterList: []
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
    'character-detail': CharacterDetail,

  },
  computed: {
    filteredCharacterListComp() {
      this.filteredCharacterList = this.characters.filter(character => {
        return character.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  },
  methods: {
    enterSearch: function () {
      this.selectedCharacter = this.filteredCharacterList[0]
    }
    }

}
</script>

<style lang="css" scoped>
/*
#character-detail {
  display: flex;
} */

</style>
