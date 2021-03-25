<template>
  <div id="app">
    <h1>Jump Game v0.10</h1>
    <button
        class="btn btn-primary btn-lg m-4"
        @click="loadGameWorld"
    >
      {{ (isGameWorld ? "Back to Settings" : "Start Game") }}
    </button>
    <div v-if="isGameWorld">
      <GameWorld
        :gameSpeed = "gameSpeed"
        :blockHeight = "blockHeight"
        :characterHeight = "characterHeight"
      ></GameWorld>
    </div>
    <form v-if="!isGameWorld">
      <h5 class="p-1">Me vs JavaScript, it's an endless battle to became a better coder and there are an interactive lessons I've learned.</h5>
        <div class="bg-light p-2">
          <p>The faster I go the harder it hits - take the time, <b>do not rush</b> in learning new things.</p>
          <div class="input-group-prepend p-1">
            <span class="input-group-text font-weight-bold">Game Speed (lower is faster)</span>
            <input v-model="gameSpeed" type="number" max="10" min="1" class="form-control font-weight-bold" aria-describedby="inputGroup-sizing-sm">
          </div>
        </div>
        <div class="p-2">
          <p>The bigger the project is, the harder to finish - <b>start small</b>, end big.</p>
          <div class="input-group-prepend p-1">
            <span class="input-group-text font-weight-bold">Block Height</span>
            <input v-model="blockHeight" type="number" max="300" min="30" class="form-control font-weight-bold" aria-describedby="inputGroup-sizing-sm">
          </div>
        </div>
        <div class="bg-light p-2">
          <p>Learning frameworks or specific libraries at the beginning is not the way to go - <b>start</b> by <b>little</b>, start from basics.</p>
          <div class="input-group-prepend p-1">
            <span class="input-group-text font-weight-bold">Character Height</span>
            <input v-model="characterHeight" type="number" max="200" min="36" class="form-control font-weight-bold" aria-describedby="inputGroup-sizing-sm">
          </div>
        </div>
      </form>
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
      blockHeight: 100, //px
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
</style>
