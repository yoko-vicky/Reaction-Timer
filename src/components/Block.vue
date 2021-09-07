<template>
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
      timer: null,
      reactionTime: 0,
    }
  },
  mounted(){
    console.log('Component mounted!')
    setTimeout(() => {
      this.showBlock = true
      console.log(this.delay)
      this.startTimer()
    }, this.delay);
  },
  methods: {
    startTimer(){
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10);
    },
    stopTimer(){
      clearInterval(this.timer)
      this.$emit('endGame', this.reactionTime)
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
