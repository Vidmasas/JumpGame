<template>
  <div id="world">
    <div
        id="character"
        :class="{jump: activeJump}"
    >
    </div>
    <div id="block"></div>
    <button @click="jumpAction" class="btn-outline-primary">Click me to JUMP!</button>
  </div>
</template>

<script>

export default {
  props: ['gameSpeed', 'blockHeight', 'characterHeight', 'isGameWorld'],
  data() {
    return {
      activeJump: false,
      gameLost: false,
      worldHeight: 400, // DO NOT CHANGE
    }
  },
  mounted() {
    // Game Elements
    const characterElement = document.getElementById("character");
    const blockElement = document.getElementById("block");
    const worldElement = document.getElementById("world");

    // Restart Game
    function restart() {
      if(this.gameLost) {
        blockElement.style.animation = 1 + "s";
        blockElement.style.display = "inline";
      }
    }

    // Games Settings based on data() variables
    worldElement.style.height = this.worldHeight + "px"
    blockElement.style.animationDuration = this.gameSpeed + "s";
    blockElement.style.width = this.blockHeight*2.8 + "px"
    blockElement.style.height = this.blockHeight + "px"
    blockElement.style.top = this.worldHeight - this.blockHeight - this.characterHeight + "px"
    characterElement.style.top = this.worldHeight - this.characterHeight + "px"
    characterElement.style.width = this.characterHeight + "px"
    characterElement.style.height = this.characterHeight + "px"

    // Game rules
    setInterval(() => {
      let characterTop = parseInt(window.getComputedStyle(characterElement).getPropertyValue("top"));
      let characterWidth = parseInt(window.getComputedStyle(characterElement).getPropertyValue("width"));
      let blockTop = parseInt(window.getComputedStyle(blockElement).getPropertyValue("top"));
      let blockLeft = parseInt(window.getComputedStyle(blockElement).getPropertyValue("left"));
      if (blockLeft < characterWidth && blockTop < characterTop) {
        this.gameLost = true;
        alert("JavaScript beat you!");
        restart();
      }
    }, 1)
  },
  methods: {
    jumpAction() {
      if (!this.activeJump) {
        const that = this;
        setTimeout(() => {
              return that.activeJump = false;
            },
            1000)
        return this.activeJump = true;
      }
    },
  },
}
</script>

<style>
#world {
  margin: auto;
  border-bottom: 1px solid black;
}
#character {
  position: relative;
  background-color: blue;
  background-image: url("https://screenshot.click/23-12-tj21u-te3f4.png");
}

.jump {
  animation: jump linear;
  animation-duration: 1s;
}

#block {
  position: relative;
  animation: block linear infinite;
  background-color: green;
  background-image: url("https://screenshot.click/23-01-q8x9s-t1wjn.png");
}

@keyframes block {
  0%{left: 3000px}
  100%{left: -400px}
}

@keyframes jump {
  0% {bottom: 300px}
  20% {top: 175px}
  50% {top: 150px}
  80% {top: 175px}
  100% {bottom: 300px}
}
</style>
