<template>
  <h1>Reaction Timer Game</h1>
  <button @click="start">play</button>
  <Block v-if="isPlaying" :delay="delay" @ended="endGame" />
  <p v-if="showResults">Reaction Time : {{ score }} ms</p>
  <Results />
</template>

<script>
import Block from "./components/Block";
import Results from "./components/Results";

export default {
  name: "App",
  components: { Results, Block },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
