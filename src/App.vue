<template>
<h1>Reaction Timer</h1>
<button @click="start" :disabled="isplaying">Play</button>
<block v-if="isplaying" :delay="delay" @end="endgame"/>
<Result v-if="showresults" :score="score" />

  
</template>

<script>

import Block from "./components/Block.vue"
import Result from "./components/Result.vue"
export default {
  name: 'App',
  components: {
    Block,Result
    
  },
  data(){
    return{
      isplaying:false,
      delay:null,
      score:null,
      showresults:false

    }
  },
  methods:{
    start(){

      this.delay=2000 + Math.random()*4000
      this.isplaying=true
      this.showresults=false
      console.log(this.delay)
    },
    endgame(reactiontimer){
     
      this.score=reactiontimer
      this.isplaying=false
       this.showresults=true


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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
