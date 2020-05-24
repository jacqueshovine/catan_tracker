<template>
  <b-row>
    <b-col>
      {{ name }}
    </b-col>
    <b-col v-for="resource in resources" v-bind:key="resource.id">
      <b-row>
        <resource :name="resource.name"></resource>
        <button v-on:click="decrement(resource)"> - </button> {{ resource.count }} <button v-on:click="increment(resource)"> + </button>
      </b-row>
    </b-col>
  </b-row>
</template>

<script>

import Resource from './Resource.vue'

export default {
  name: 'Player', // Component name
  components: {
    Resource
  },
  props: {
    name: String // Player name
  },
  data() {
    return {
      resources: [
        {id: 1, name:'Wood', count: 0},
        {id: 2, name:'Brick', count: 0},
        {id: 3, name:'Wheat', count: 0},
        {id: 4, name:'Ore', count: 0},
        {id: 5, name:'Sheep', count: 0},
      ]
    }
  },
  methods: {
    increment(resource) {
      resource.count += 1
    },
    decrement(resource) {
      if (resource.count > 0) {
        resource.count -= 1
      }
    }
  }
}
</script>