<template>
  <b-row>
    <b-col cols="1">{{ name }}</b-col>
    <b-col cols="1" v-for="resource in resources" v-bind:key="resource.id">
      <b-button v-on:click="decrement(resource, 1)" variant="danger"> - </b-button> {{ resource.count }} <b-button v-on:click="increment(resource, 1)" variant="success"> + </b-button>
    </b-col>
    <b-col cols="5">
      <b-button class="btn-action" v-on:click="buildRoad()">Build road</b-button>
      <b-button class="btn-action">Build settlement</b-button>
      <b-button class="btn-action">Build city</b-button>
      <b-button class="btn-action">Draw card</b-button>
    </b-col>
    <b-col cols="1">
      Score
    </b-col>
  </b-row>
</template>

<script>

// import Resource from './Resource.vue'

export default {
  name: 'Player', // Component name
  components: {
    // Resource
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
    increment(resource, n) {
      resource.count += n
    },
    decrement(resource, n) {
      if (resource.count > 0) {
        resource.count -= n
      }
    },
    hasResources(name, amount) {
      return this.resources.filter((r) => {
        return r.name === name
      })[0].count >= amount
    },
    // Road = 1Wood, 1Brick
    buildRoad() {
      if (!this.hasResources('Wood', 1)) {
        return
      }

      if (!this.hasResources('Brick', 1)) {
        return
      }

      this.resources.map((r) => {
        if (r.name === 'Wood' || r.name === 'Brick') {
          this.decrement(r, 1)
        }
      })
    }
  }
}
</script>