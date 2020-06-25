<template>
  <div>
    <h2>Favourites</h2>
    <ul>
      
      <li v-for="(fave, key) in favouriteBeers" :key='key'>{{ fave.name }}  <button type="submit" v-on:click="removeFavorite(fave.name)">Remove</button>  </li>
    </ul>
  </div>
</template>

<script>
import { eventBus } from "../main";
export default {
  name: "favouriteslist",
  data() {
    return {
      favouriteBeers: []
    };
  },
  mounted() {
    eventBus.$on("beer", beer => {
       console.log('adding beer');
     if(!this.favouriteBeers.includes(beer)) {
        this.favouriteBeers.push(beer);
      }
      
    });
  },
  methods: {
    removeFavorite(name) {
      let beer = this.favouriteBeers.find(beer => beer.name == name);
       this.favouriteBeers.splice(this.favouriteBeers.indexOf(beer), 1);
    }
  }
};
</script>

<style>
</style>