<template>
  <div id="app">
    <h1>Jump Game v0.10</h1>
    <button
        class="btn btn-primary btn-lg" style="margin-bottom: 10px"
        @click="loadGameWorld"
    >
      {{ (isGameWorld ? "Back to Settings" : "Start Game") }}
    </button>
    <div v-if="isGameWorld">
      <GameWorld
        :gameSpeed = "gameSpeed"
        :blockWidth = "blockWidth"
        :blockHeight = "blockHeight"
        :characterWidth = "characterWidth"
        :characterHeight = "characterHeight"
      ></GameWorld>
    </div>
    <div v-if="!isGameWorld" class="settings col-sm-2">
      <div class="input-group-prepend">
        <span class="input-group-text">Game Speed</span>
        <input v-model="gameSpeed" type="number" class="form-control" aria-describedby="inputGroup-sizing-sm">
      </div>
      <div class="input-group-prepend">
        <span class="input-group-text">Block Width</span>
        <input v-model="blockWidth" type="number" class="form-control" aria-describedby="inputGroup-sizing-sm">
      </div>
      <div class="input-group-prepend">
        <span class="input-group-text">Block Height</span>
        <input v-model="blockHeight" type="number" class="form-control" aria-describedby="inputGroup-sizing-sm">
      </div>
      <div class="input-group-prepend">
        <span class="input-group-text">Character Width</span>
        <input v-model="characterWidth" type="number" class="form-control" aria-describedby="inputGroup-sizing-sm">
      </div>
      <div class="input-group-prepend">
        <span class="input-group-text">Character Height</span>
        <input v-model="characterHeight" type="number" class="form-control" aria-describedby="inputGroup-sizing-sm">
      </div>
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
