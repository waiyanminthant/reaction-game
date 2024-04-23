<template>
  <h1>How fast can you catch me?</h1>
  <button class="btn" @click="startGame" :disabled="isPlaying">
    {{ btnText }}
  </button>
  <div v-if="isPlaying">
    <ClickBlock :delay="delay" @endGame="endGame" />
  </div>
  <GameResult :reactionTime="reactionTime" v-if="showResult" />
</template>

<script>
import ClickBlock from "./components/ClickBlock.vue";
import GameResult from "./components/GameResult.vue";

export default {
  components: {
    ClickBlock,
    GameResult,
  },

  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: 0,
      showResult: false,
      btnText: "Lets Go!",
    };
  },
  methods: {
    startGame() {
      this.isPlaying = true;
      this.btnText = "Wait for it..."
      this.showResult = false;
      this.delay = 1000 + Math.random() * 3000;
    },
    endGame(reactionTime) {
      this.reactionTime = reactionTime;
      this.btnText = "Play Again!"
      this.showResult = true;
      this.isPlaying = false;
    },
  },
};
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
.btn {
  border-radius: 10px;
  border: 0px;
  font-family: Arial;
  color: #ffffff;
  font-size: 20px;
  background: #3498db;
  padding: 10px 20px 10px 20px;
  text-decoration: none;
}

.btn:hover {
  background: #3cb0fd;
}

.btn:disabled{
  background: grey;
}
</style>
