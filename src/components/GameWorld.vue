<template>
  <div class="world"
       @click="jumpAction"
  >
    <div
        id="character"
        :class="{jump: activeJump}"
    >

    </div>
    <div id="block"></div>
    <div>{{ score }}</div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      activeJump: false,
      counter: 0,
      score: 0,
      jumpSpeed: 1000, //ms
      gameSpeed: 2, //s
      blockWidth: 40, //px
      blockHeight: 40, //px
      blockTop: 310, //px
      blockLeft: 480 //px
    }
  },
  mounted() {
    const characterElement = document.getElementById("character");
    const blockElement = document.getElementById("block");
    blockElement.style.animationDuration = this.gameSpeed + "s";
    blockElement.style.width = this.blockWidth + "px"
    blockElement.style.left = this.blockLeft + "px"
    blockElement.style.height = this.blockHeight + "px"
    blockElement.style.top = this.blockTop + "px"

    //Score rules
    setInterval(() => {
      let characterTop = parseInt(window.getComputedStyle(characterElement).getPropertyValue("top"));
      let characterWidth = parseInt(window.getComputedStyle(characterElement).getPropertyValue("width"));
      let blockTop = parseInt(window.getComputedStyle(blockElement).getPropertyValue("top"));
      let blockLeft = parseInt(window.getComputedStyle(blockElement).getPropertyValue("left"));
      let blockWidth = parseInt(window.getComputedStyle(blockElement).getPropertyValue("width"));
      if (blockLeft < characterWidth && blockLeft > 0 && characterTop >= blockTop) {
        blockElement.style.animation = "none";
        blockElement.style.display = "none";
        alert("You lose, your score is " + this.score);
        this.score = 0;
      } else if (blockLeft < characterWidth && blockLeft > 0 && characterTop < blockTop) {
        this.counter++;
        this.score = Math.floor(this.counter/this.gameSpeed/blockWidth*10);
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
.world {
  margin: auto;
  width: 1000px;
  height: 400px;
  border: 1px solid black;
}
#character {
  height: 50px;
  width: 20px;
  position: relative;
  top: 350px;
  background-color: blue;
}

.jump {
  animation: jump linear;
  animation-duration: 1s;
}

#block {
  position: relative;
  animation: block linear infinite;
  animation-duration: 2s;
  background-color: green;
}

@keyframes block {
  0%{left: 900px}
  100%{left: -40px}
}

@keyframes jump {
  0% {bottom: 300px}
  20% {top: 175px}
  50% {top: 150px}
  80% {top: 175px}
  100% {bottom: 300px}
}

</style>