<template>
  <div id="world"
       @click="jumpAction"
  >
    <div
        id="character"
        :class="{jump: activeJump}"
    >

    </div>
    <div id="block"></div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      activeJump: false,
      worldHeight: 400, // DO NOT CHANGE
      // Game settings
      jumpSpeed: 1000, //ms // TBA
      gameSpeed: 2, //s higher is slower
      blockWidth: 280, //px
      blockHeight: 80, //px // TBA
      characterWidth: 36, //px
      characterHeight: 36, //px
    }
  },
  mounted() {
    // Game Elements
    const characterElement = document.getElementById("character");
    const blockElement = document.getElementById("block");
    const worldElement = document.getElementById("world");

    // Games Settings based on data() variables
    worldElement.style.height = this.worldHeight + "px"
    blockElement.style.animationDuration = this.gameSpeed + "s";
    blockElement.style.width = this.blockWidth + "px"
    blockElement.style.height = this.characterHeight*2 + "px"
    blockElement.style.top = this.worldHeight - this.characterHeight*3 + "px"
    characterElement.style.top = this.worldHeight - this.characterHeight + "px"
    characterElement.style.width = this.characterWidth + "px"
    characterElement.style.height = this.characterHeight + "px"

    //Score rules
    setInterval(() => {
      let characterTop = parseInt(window.getComputedStyle(characterElement).getPropertyValue("top"));
      let characterWidth = parseInt(window.getComputedStyle(characterElement).getPropertyValue("width"));
      let blockTop = parseInt(window.getComputedStyle(blockElement).getPropertyValue("top"));
      let blockLeft = parseInt(window.getComputedStyle(blockElement).getPropertyValue("left"));
      if (blockLeft < characterWidth && blockTop < characterTop) {
        blockElement.style.animation = "none";
        blockElement.style.display = "none";
        alert("You lose");
      }
    }, 1)

  },
  methods: {
    jumpAction() {
      const that = this
      setTimeout(() => {
            return that.activeJump = !that.activeJump;
          },
          this.jumpSpeed)
      return this.activeJump = !this.activeJump;
    },
  },
}
</script>

<style lang="scss">
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
  0%{left: 2000px}
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