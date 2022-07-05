<template>
<div class="backGround">
  <div class="container">
    <h1>My Reaction Timer</h1>
    <p v-if="!isPlaying">遊戲說明：按下開始之後，快速點擊出現之方框，測試你的反應速度！</p>
    <button @click="startGame" :disabled="isPlaying">開始 !</button>
    
    <block v-if="isPlaying" :delay="delay" @endGame="endGame" />
    <results :score="score" v-if="showResults" />
  </div>
</div>

</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue';

export default {
  name: 'App',
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods:{
    startGame(){
      this.isPlaying = true;
      this.delay = 1000 + Math.random() * 5000;
      this.showResults = false;
    },
    endGame(reactionTime){
      this.isPlaying = false;
      this.score = reactionTime
      this.showResults = true
    }
  },
  components: {
    Block,
    Results,
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  padding:0;
  margin:0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.backGround {
  background-color: pink;
  width:100vw;
  height:100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  
  
}
.container {
  background-color: #fff;
  width:70vw;
  height:80vh;
  border-radius: 2rem;
  padding: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
button{
  padding: 0.7rem 1rem;
  background-color: pink;
  border: none;
  color: white;
  font-weight: 700;
  font-size:1.2rem;
  cursor: pointer;
  margin: 2.5rem 0rem;
}
button:disabled{
  border: 1px solid #cccccc;
  background-color: #cccccc;
  color: white;
  cursor: not-allowed;
}
p{
  padding:1rem 0rem;
}
</style>
