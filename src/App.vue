<template>
  <h1>Hello world</h1>
  <button @click="start" :disabled="isPlaying">Start Game</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <!-- <p v-if="showScore">Reacton Time {{ score }} ms</p> -->
  <Result v-if="showScore" :score="score" />
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';
export default {
  name: 'App',
  components: {
    Block,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
    },
    endGame(reactionTimer) {
      this.score = reactionTimer;
      this.isPlaying = false;
      this.showScore = true;
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
  color: #444;
  margin-top: 60px;
}
button {
  background: lightgreen;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
