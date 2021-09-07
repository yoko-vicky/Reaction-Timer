<template>
  <h1>Reaction Timer</h1>
  <button @click="startGame" :disabled="isPlaying">Play</button>
  <Block :delay="delay" v-if="isPlaying" @restart="restartGame" />
</template>

<script>
import Block from './components/Block.vue'

export default {
  name: 'App',
  components: { Block },
  data(){
    return {
      isPlaying: false,
      delay: null,
    }
  },
  methods: {
    startGame(){
      this.delay = 2000 + Math.random() * 5000 // 2000 - 5000 ms
      this.isPlaying = true
    },
    restartGame(){
      this.isPlaying = false
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
