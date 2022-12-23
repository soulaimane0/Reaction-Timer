<template>
    <h1>{{ title }}</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <!-- <p v-if="showResault">The Reaction Time is : {{ score }}  s </p> -->

    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
    <Resault v-if="showResault" :score="score" @hideResault="hideResault"/>
</template>

<script>
import Block from './components/Block.vue'
import Resault from './components/Resault.vue'
export default {
  name: 'App',
  data(){
    return {
      title:'Reation Timer (:',
      isPlaying: false,
      delay: null,
      score:null,
      showResault: false,
    }
  },
  methods:{
    start(){
      this.isPlaying = true;
      this.delay = 1600 + Math.random()*4000;
      this.showResault=false;
      console.log(this.delay)
    },
    endGame(reactionTime){
      this.showResault = true;
      this.score = reactionTime;
      this.isPlaying = false;
      
    },
    hideResault(){
      this.showResault = false;
    }
  },
  components: {
    Block,
    Resault
  }
}
</script>

<style>
body{
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  padding: 12px 28px;
  border-radius: 8px;
  border: none;
  background: rgb(122, 216, 122);
  cursor:pointer;
}
</style>
