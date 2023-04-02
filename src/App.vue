<template>
  <h1 class="h1">Ninja React Timer</h1>
  <button class="btn" @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <Results v-if="showResults" :score="score" ></Results>
  <!-- <p v-if="showResults">Reaction time: {{ score }} ms</p> -->
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue';

export default {
  name : 'App',
  components : {Block, Results},
  data () {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods : {
    start () {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults= false;
    },
    endGame (reactionTime) {
        this.score = reactionTime;
        this.isPlaying = false;
        this.showResults= true;
    },
  }

}
</script>

<style>
  #app {
    font-family: Avenir, Arial, Helvetica, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osk-font-smoothing: grayscale;
    text-align: center;
    color: #444;
  }


</style>