<template>
  <div v-if="showResult">
    <p>Time: 00,000!</p>
    <button @click="restartGame">Restart Game!</button>
  </div>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
  props: ['delay'],
  data(){
    return {
      showBlock: false,
      showResult: false
    }
  },
  mounted(){
    console.log('Component mounted!')
    setTimeout(() => {
      this.showBlock = true
      console.log(this.delay)
    }, this.delay);
  },
  updated(){
    console.log('Component updated!')
    // setTimer
  },
  unmounted(){
    console.log('Component unmounted!')
  },
  methods: {
    stopTimer(){
      console.log('timer stop')
      this.showResult = true
    },
    restartGame(){
      this.$emit('restart')
    }
  }
}
</script>

<style>
  .block {
    width: 400px;
    border-radius: 20px;
    background:  #0faf87;;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>
