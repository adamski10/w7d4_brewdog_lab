<template>
  <div id="app">
    <beer v-for="(beer, key) in beers" :beer="beer"/>
  </div>
</template>

<script>
import beer from './components/Beer.vue';

export default {
  name: 'App',
  data(){
    return {
      beers: []
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)
  },
  components: {
    beer
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
