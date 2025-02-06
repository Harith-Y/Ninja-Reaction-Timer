<template>
  <div class="container">
    <h1 class="header">Ninja Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying" @restart="start"> Play </button>
    <Block v-if="isPlaying" :delay="delay" @stop="stopGame"/>
    <Results v-if="showResults" :score="score"/>
  </div>
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

#app, html, body {
  height: 100%;
  margin: 0;
  padding: 0;
  background-color: #e0f7fa;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  background-color: #405255; /* Light cyan background for the page */
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  background-color: #6f929e;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.header {
  font-size: 2.5em;
  margin-bottom: 20px;
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
  transition: background-color 0.3s ease;
}

button:disabled {
  opacity: 0.2;
  cursor: not-allowed;
}

button:hover {
        background-color: #0a8f6a;
    }
</style>
