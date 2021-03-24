<template>
  <div id="app">
    <h1>Jump Game v0.10</h1>
    <button @click="loadGameWorld">{{ (isGameWorld ? "Back to Settings" : "Start Game") }}</button>
    <div v-if="isGameWorld">
      <GameWorld
        :gameSpeed = "gameSpeed"
        :blockWidth = "blockWidth"
        :blockHeight = "blockHeight"
        :characterWidth = "characterWidth"
        :characterHeight = "characterHeight"
      ></GameWorld>
    </div>
    <div v-if="!isGameWorld" class="settings">
      <div><label>Game speed </label><input type="number" v-model="gameSpeed"><span> higher is slower</span></div>
      <div><label>Block width </label><input type="number" v-model="blockWidth"><span> px</span></div>
      <div><label>Block height </label><input type="number" v-model="blockHeight"><span> px</span></div>
      <div><label>Character width </label><input type="number" v-model="characterWidth"><span> px</span></div>
      <div><label>Character height </label><input type="number" v-model="characterHeight"><span> px</span></div>
    </div>
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
      isGameWorld: false,
      // Game settings
      gameSpeed: 4, //s higher is slower
      blockWidth: 280, //px
      blockHeight: 100, //px
      characterWidth: 36, //px
      characterHeight: 36, //px
    }
  },
  methods: {
    loadGameWorld() {
      this.isGameWorld = !this.isGameWorld;

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

.settings {

}
</style>
