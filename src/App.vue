<template>
  <h1>Reaction Timer</h1>
  <Results v-if="showResults" :score="score" />
  <button @click="startGame" :disabled="isPlaying">Play</button>
  <Block :delay="delay" v-if="isPlaying" @endGame="endGame" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    startGame(){
      this.showResults = false
      this.delay = 2000 + Math.random() * 5000 // 2000 - 5000 ms
      this.isPlaying = true
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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
</style>
