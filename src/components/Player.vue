<template>
  <b-row>
    {{ playerName }}
    <label v-for="item in items" v-bind:key="item.id">
      <resource :resourceName="item"/>
    </label>
  </b-row>
</template>

<script>

import Resource from './Resource.vue'

export default {
  name: 'Player',
  components: {
    Resource
  },
  props: {
    playerName: String
  },
  data() {
    return {
      items: ['wood', 'brick', 'wheat', 'ore', 'sheep']
    }
  }
}
</script>