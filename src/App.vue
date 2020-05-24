<template>
  <b-container fluid id="app">
    <h1>Catan tracker</h1>
    <!--
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    -->
    <div>
      <h2>Players</h2>
      <b-row>
        <b-col v-for="player in players" v-bind:key="player.id" v-bind:name="player.name">
          <input v-model="player.name">
        </b-col>
      </b-row>
    </div>
    <hr>
    <h2>Resources</h2>
    <player v-for="player in players" v-bind:key="player.id" v-bind:name="player.name"></player>
    <!-- 
    <b-row v-for="player in players" v-bind:key="player.id">
      <b-col>{{ player.name }}</b-col>
      <b-col v-for="resource in resources" v-bind:key="resource.id">
        <resource :resourceName="resource"/>
      </b-col>
      <hr>
    </b-row>
    -->

  </b-container>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Player from './components/Player.vue'
// import Resource from './components/Resource.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Player,
    // Resource
  },
  data() {
    return {
      players: [
        {id: 1, name: 'Player 1', score: 0},
        {id: 2, name: 'Player 2', score: 0},
        {id: 3, name: 'Player 3', score: 0},
        {id: 4, name: 'Player 4', score: 0},
      ],
      resources: ['wood', 'brick', 'wheat', 'ore', 'sheep']
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

label {
  margin-bottom:0;
}
</style>
