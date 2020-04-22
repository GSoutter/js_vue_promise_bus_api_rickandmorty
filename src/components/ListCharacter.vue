<template lang="html">
  <li v-on:click="handleClick">{{character.name}}</li>
</template>

<script>
import {eventBus} from "../main.js"


export default {
  name: 'list-character',
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
