<template>
<div>
  <b-row>
    <b-col cols="1">{{ name }}<b-button v-on:click="resetResources()">Reset</b-button></b-col>
    <b-col cols="2" v-for="resource in resources" v-bind:key="resource.id">
      <b-button v-on:click="decrement(resource, 1)" variant="danger"> - </b-button> <span class="resourceCount">{{ resource.count }}</span> <b-button v-on:click="increment(resource, 1)" variant="success"> + </b-button>
    </b-col>

    <b-col cols="1">
      Score
    </b-col>
  </b-row>
  <b-row>
    <b-col>
      <b-button class="btn-action" variant="info" v-on:click="buildRoad()">Build road</b-button>
      <b-button class="btn-action" variant="info" v-on:click="buildSettlement()">Build settlement</b-button>
      <b-button class="btn-action" variant="info" v-on:click="buildCity()">Build city</b-button>
      <b-button class="btn-action" variant="info" v-on:click="drawCard()">Draw card</b-button>
    </b-col>
  </b-row>
</div>
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
    setResource(resource, n) {
      resource.count = n
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
    },
    // Settlement = 1Wood, 1Brick, 1Sheep, 1Wheat
    buildSettlement() {
      if (!this.hasResources('Wood', 1)) {
        return
      }

      if (!this.hasResources('Brick', 1)) {
        return
      }

      if (!this.hasResources('Sheep', 1)) {
        return
      }
  
      if (!this.hasResources('Wheat', 1)) {
        return
      }

      this.resources.map((r) => {
        if (r.name !== 'Ore') {
          this.decrement(r, 1)
        }
      }) 
    },
    // City = 2Wheat, 3Ore
    buildCity() {
      if (!this.hasResources('Wheat', 2)) {
        return
      }

      if (!this.hasResources('Ore', 3)) {
        return
      }

      this.resources.map((r) => {
        if (r.name === 'Wheat') {
          this.decrement(r, 2)
        }

        if (r.name === 'Ore') {
          this.decrement(r, 3)
        }
      })
    },
    // Draw card = 1Sheep, 1 Wheat, 1Ore
    drawCard() {
      if (!this.hasResources('Sheep', 1)) {
        return
      }

      if (!this.hasResources('Wheat', 1)) {
        return
      }

      if (!this.hasResources('Ore', 1)) {
        return
      }

      this.resources.map((r) => {
        if (r.name === 'Sheep' || r.name === 'Wheat' || r.name === 'Ore') {
          this.decrement(r, 1)
        }
      })
    },
    resetResources() {
      this.resources.map((r) => {
        this.setResource(r, 0)
      })
    }
  }
}
</script>