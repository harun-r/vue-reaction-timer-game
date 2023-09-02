<template>
  <div class="header">
    <h3>Ninja Reaction Timer</h3>
    <button @click="start" :disabled="isPlaying">play</button>

  </div>
  <div class="block-wrap" v-if="isPlaying">
    <Block :delay="delay" @end="endGame"/>
  </div>
  <div class="result-block" v-if="showResult">
    <Result :score="score"/>
  </div>
</template>
<script>
import Block from "@/components/timer/Block.vue";
import Result from "@/components/timer/Result.vue";
export default {
  name: "App",
  components: {
    Block,
    Result
  },
  data() {
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
}

</script>

<style scoped>

</style>
