<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying" @restart="start"> Play </button>
  <Block v-if="isPlaying" :delay="delay" @stop="stopGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>

import Results from "./components/Results.vue"
import Block from "./components/Block.vue"

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.showResults = false
      this.isPlaying = true
      // console.log(this.delay)
    },
    stopGame(reactTime) {
      this.score = reactTime
      this.isPlaying = false
      this.showResults = true
      console.log("Game Over!")
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
  color: #444;
  margin-top: 60px;
}

button {
  padding: 8px 16px;
  font-size: 1.2em;
  background: #0faf87;
  color: white;
  letter-spacing: 1px;
  border-radius: 4px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
