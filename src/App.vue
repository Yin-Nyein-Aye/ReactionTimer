<template>
  <h1>How fast you are?</h1>
  <button @click="playGame" :disabled="isPlaying">play</button>
  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame" />
  </div>
  <div v-if="end">
    <Result :score="score" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
      end:false
    }
  },
  methods:{
    playGame(){
      this.isPlaying = true;
      this.delay=2000+Math.random()*5000;
    },
    endGame(score){
      this.score=score
      this.isPlaying=false
      this.end = true
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
