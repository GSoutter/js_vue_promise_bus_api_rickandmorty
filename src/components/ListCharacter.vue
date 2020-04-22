<template lang="html">
  <li v-on:click="handleClick">{{character.name}}</li>
</template>

<script>
export default {
  name: 'list-character',
  props: ['character'],
  methods: {}
}
</script>

<style lang="css" scoped>
</style>
