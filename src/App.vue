<template>
  <div id="app">
    <div id="favlist">
      <favouriteslist />
    </div>
    <beer v-for="(beer, key) in beers" :beer="beer"/>
  </div>
  
</template>

<script>
import beer from './components/Beer.vue';
import favouriteslist from './components/FavouritesList.vue';
import { eventBus } from './main.js'

export default {
  name: 'App',
  data(){
    return {
      beers: [],
      favouriteBeers: []
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)
  },
  components: {
    "beer": beer,
    "favouriteslist": favouriteslist
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
