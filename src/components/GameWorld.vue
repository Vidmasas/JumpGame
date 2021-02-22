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
      blockSpeed: 2,
      loopSpeed: 200
    }
  },
  mounted() {
    let characterElement = document.getElementById("character");
    let blockElement = document.getElementById("block");

    setInterval(() => {
      const characterTop = parseInt(window.getComputedStyle(characterElement).getPropertyValue("top"));
      const blockLeft = parseInt(window.getComputedStyle(blockElement).getPropertyValue("left"));
      if (blockLeft < 20 && blockLeft > 0 && characterTop >= 310) {
        blockElement.style.animation = "none";
        blockElement.style.display = "none";
        alert("You lose, your score is " + this.score);
        this.score = 0;
      } else if (blockLeft < 20 && blockLeft > 0 && characterTop < 310) {
        this.counter++;
        this.score = Math.floor(this.counter/8);
      }
    }, 1)

    setInterval(() => {
      this.blockSpeed = Math.random() + this.blockSpeed;
      blockElement.style.animationDuration = this.blockSpeed + "s";
      console.log(blockElement.style.animationDuration = this.blockSpeed + "s")
      this.loopSpeed = parseFloat(blockElement.style.animationDuration)*100;
      console.log(this.loopSpeed)
    },this.loopSpeed)
  },
  methods: {
    jumpAction() {
      const that = this
      setTimeout(() => {
            return that.activeJump = !that.activeJump;
          },
          500)
      return this.activeJump = !this.activeJump;
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
  animation: jump linear 500ms;
}

#block {
  height: 40px;
  width: 40px;
  background-color: green;
  position: relative;
  top: 310px;
  left: 480px;
  animation: block linear infinite;
}

@keyframes block {
  0%{left: 900px}
  100%{left: -40px}
  //@for $i from 1 through 10 {
  //#{($i * 0.5%)} {
  //  transform: rotate((480 * 1deg));
  // }
  //}
}

@keyframes jump {
  0% {bottom: 300px}
  20% {top: 200px}
  50% {top: 150px}
  80% {top: 200px}
  100% {bottom: 300px}
}

</style>
