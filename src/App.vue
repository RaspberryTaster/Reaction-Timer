<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" v-bind:delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score = "score"/>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Block from './components/Block.vue';
import Results from './components/Results.vue';

export default defineComponent({
  // Other options for the component
  components: {
    Block,Results
  },

  setup() {
    const isPlaying = ref(false);
    const delay = ref(0);
    const score = ref(0);
    const showResults = ref(false);
    // Your logic for the start function
    const data = () =>{
      isPlaying.value = false;
      delay.value = 0;
      score.value = 0;
      showResults.value = false;
      return{isPlaying,delay}
    }
    const endGame = (reactionTime: number) => {
      score.value = reactionTime
      isPlaying.value = false;
      showResults.value = true;       
    }
    const start = () => {
      //random between 0 and 5000
      delay.value = 2000 + Math.random()*5000;
      isPlaying.value = true;
      showResults.value = false;  
    };

    // Return any data or methods needed by the template
    return {
      start,isPlaying,delay,endGame,score,showResults
      // You can add more properties or methods here if needed
    };
  },
});
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
  opacity:0.2;
  cursor: not-allowed;
}
</style>
