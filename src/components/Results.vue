<template>
  <p>ReactionTime: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ['score'],
  data(){
    return {
      rank: null
    }
  },
  mounted(){
    if(this.score < 460){
      this.rank = 'Fantastic Ninja!'
    } else if(this.score < 1000){
      this.rank = 'Normal Ninja'
    } else {
      this.rank = 'Train harder!'
    }
  }
}
</script>

<style>
.rank{
  font-size: 1.4em;
  color: salmon;
  font-weight: bold;
}
</style>
