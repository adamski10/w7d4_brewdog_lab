<template>
  <ul>
    <li v-for="(fave, key) in favoriteBeers">{{ fave.name }}</li>
  </ul>
</template>

<script>
import { eventBus } from '../main';
export default {
  name: "favouriteslist",
  data() {
    return {
      favoriteBeers: []
    };
  },
  mounted() {
    eventBus.$on('beer', (beer) => {
      this.favoriteBeers.push(beer);
    })
  }
};
</script>

<style>
</style>