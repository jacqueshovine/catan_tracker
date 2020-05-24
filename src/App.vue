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
    <div>
      <b-row>
        <b-col class="header" v-for="header in headers" v-bind:key="header.key" :cols="header.cols">{{ header.title }}</b-col>
      </b-row>
    </div>
    <div v-for="player in players" v-bind:key="player.id" >
      <player class="playerRow" v-bind:name="player.name"></player>
    </div>
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
      headers: [
        {title: 'Name', cols: 1},
        {title: 'Wood', cols: 1},
        {title: 'Brick', cols: 1},
        {title: 'Wheat', cols: 1},
        {title: 'Ore', cols: 1},
        {title: 'Sheep', cols: 1},
        {title: 'Actions', cols: 5},
        {title: 'Score', cols: 1}
      ]
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

.header {
  font-weight: bold;
}

.playerRow {
  margin-top:20px;
}

.btn-action {
  margin:0 5px;
}

label {
  margin-bottom:0;
}
</style>
