<template>
  <h1>Reaction timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @theEnd="endGame"/>
  <Results v-if="showScore" :score="score"/>
  <!-- <p v-if="showScore">Reaction time = {{score}} ms</p> -->
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showScore = false
    },
    endGame(reactionT){
      this.score = reactionT
      this.isPlaying = false
      this.showScore = true
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: gray;
  margin-top: 60px;
}
button{
  background-color: seagreen;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: .2;
  cursor: not-allowed;
}
</style>
