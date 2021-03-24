<template>
  <div id="app">
    <h1>Jump Game v0.10</h1>
    <GameWorld
      :gameSpeed = "gameSpeed"
      :blockWidth = "blockWidth"
      :blockHeight = "blockHeight"
      :characterWidth = "characterWidth"
      :characterHeight = "characterHeight"
    ></GameWorld>
  </div>
</template>

<script>
import GameWorld from './components/GameWorld.vue'

export default {
  name: 'App',
  components: {
    GameWorld
  },
  data() {
    return {
      // Game settings
      gameSpeed: 2, //s higher is slower
      blockWidth: 280, //px
      blockHeight: 120, //px
      characterWidth: 36, //px
      characterHeight: 36, //px
    }
  },
  methods: {

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
</style>
