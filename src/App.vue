<template>
  <div id="app">
    <h1>Jump Game v0.10</h1>
    <GameWorld/>
  </div>
</template>

<script>
import GameWorld from './components/GameWorld.vue'

export default {
  name: 'App',
  components: {
    GameWorld
  },
  methods: {
    test() {
      console.log("it Works")
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
