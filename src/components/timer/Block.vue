<template>
  <div class="block" v-if="showBlock" @click="StopTimer">
    <span>Click me</span>
  </div>
</template>

<script>
export default {
  name: "Block",
  props:{
    delay: null
  },
  data() {
    return{
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(()=>{
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
   methods: {
    startTimer(){
      this.timer = setInterval(()=>{
        this.reactionTime += 10
      }, 10)
    },
    StopTimer(){
      clearInterval(this.timer);
      this.$emit('end', this.reactionTime)
    }
   }
}
</script>

<style scoped>
.block{
  width: 500px;
  height: 300px;
  background-color: darkcyan;
  border-radius: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 15px;

}
</style>