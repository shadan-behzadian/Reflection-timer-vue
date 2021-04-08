<template>
  <h1>Vue reaction game</h1>
  <button @click="handleClick" v-bind:disabled="isPlaying" class="startButton">
    Start
  </button>
  <Block v-if="isPlaying" v-bind:delay="delay" @end="endGame" />
  <Results v-if="showResults" v-bind:score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return { isPlaying: false, delay: null, score: null, showResults: false };
  },
  methods: {
    handleClick() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      console.log(this.delay);
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
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
.startButton {
  width: 80px;
  height: 50px;
  border-radius: 10px;
  font-size: 1rem;
  background: rgb(170, 136, 169);
  cursor: pointer;
}

.startButton[disabled] {
  cursor: not-allowed;
}
</style>
