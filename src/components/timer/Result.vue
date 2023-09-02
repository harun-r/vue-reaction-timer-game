<template>
  <p> Reaction time: {{score}} ms</p>
  <p>{{rank}}</p>
</template>
<script>
export default {
  name: "Result",
  props:{
    score: null
  },
  data(){
    return{
      rank: null
    }
  },
  mounted() {
    this.calculateRank()
  },
  methods:{
    calculateRank(){
      if(this.score < 250){
        this.rank = 'Wow, you are very fast!'
      } else if(this.score < 400){
        this.rank = 'You are faster'
      } else {
        this.rank = 'You are average'
      }
    }
  }
}
</script>
<style scoped></style>