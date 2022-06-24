<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1> Reaction Timer Game </h1>
  <!--When user clicks play button, start() method is fired!  , isPlaying is set to true -->
   <!--Button is disabled while game is in play-->
  <button @click="start" :disabled="isPlaying">PLAY</button>
  
  <!--Only show when is playing is clicked-->
  <!---end was emited from block component (stopTimer()) method-->
  <Block  v-if="isPlaying" :delay="delay"  @end="endGame"  />

  <!--shows the component if show results is true, at the end of the game-->
  <Results v-if="showResults" :score="score"/>

  
    
</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',


// Declare variables here 
  data(){
    return{

      // initialize variables 
      isPlaying: false,
      delay: null,
      score:null, 
      showResults: false

    }
  },
  // call components here 
  components: {
     Block,
     Results
  },
  methods:{
    start(){
      // generates a random ms between 0 and 7000 miliseconds 
      this.delay = 2000 + Math.random() * 5000;
      //When user clicks play button , isPlaying is set to true 
      this.isPlaying = true;
      //set showResults to false when a new game starts
      this.showResults = false;
      
    },

    // reactionTime is from the Block component , it was emitted by stopTimer method
    endGame(reactionTime){
        //set score equal reactionTime
      this.score = reactionTime;
      // game is over so set isPlaying back to false 
      this.isPlaying = false;
      // show results at the end of the game
      this.showResults = true;


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
  background: #0faf87;
  color:white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor:pointer;
  margin: 10px;
}

button[disabled]{
  opacity: 0.2;
  cursor:not-allowed;
}
</style>
