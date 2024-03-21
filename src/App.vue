<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="this.delay" @end="endGame"/>
  
  <Result :score="score" v-if="showResult"/>
</template>

<script>

import Block from './components/Block.vue'
import Result from './components/Result.vue'
export default {
  name: 'App',
  components: {
   Block,Result
  },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:0,
      showResult:false
    }
  },
  methods:{
    endGame(getValue){
      this.showResult=true
      this.score=getValue
      this.isPlaying = false
    },
    start(){
      this.showResult=false
      this.isPlaying = true,
      this.delay=2000+Math.random() * 5000
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
button{
  background:  #0faf78;
  color:white;
  border:none;
  padding:8px 16px;
  border-radius: 4px;
  font-size:16px;
  letter-spacing: 1px;
  cursor:pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
