<template>
  <h1>How fast can you catch me?</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame" />
  </div>
  <div v-if="end">
    <Result :score="score" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      end: false
    }
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000+Math.random()*5000;
      this.end = false
    },
    endGame(score) {
      this.score = score;
      this.isPlaying = false;
      this.end = true
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
  color: #7532a2;
  margin-top: 60px;
}
button {
  background: #7532a2;
  color: #fff;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
}
:disabled {
    cursor: not-allowed;
    opacity: 0.5;
}
</style>
