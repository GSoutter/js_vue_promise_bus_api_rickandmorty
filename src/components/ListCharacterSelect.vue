<template lang="html">
  <option v-bind:value="character">{{character.name}}</option>
</template>

<script>
import {eventBus} from "../main.js"


export default {
  name: 'list-character-select',
  props: ['character'],

  methods: {
    handleClick(){
      // console.log('click', this.character);
      eventBus.$emit('character-selected', this.character)
    }
  }
}

</script>

<style lang="css" scoped>
</style>
