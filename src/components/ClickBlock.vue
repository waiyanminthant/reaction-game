<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <p>Click Here!</p>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      reactionTime: 0,
      timer: null,
    };
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.reactionTime)
    },
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
};
</script>

<style>
.block {
  background-color: aqua;
  border-radius: 12px;
  font-weight: bolder;
  width: 400px;
  height: 300px;
  margin: 20px auto;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>