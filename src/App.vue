<template>
  <h1>Ninja React Rimer</h1>
  <br>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay"></Block>
</template>

<script>
import Block from './components/Block.vue'

export default {
  name : 'App',
  components : {Block},
  data () {
    return {
      isPlaying: false,
      delay: null,

    }
  },
  methods : {
    start () {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
    }
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