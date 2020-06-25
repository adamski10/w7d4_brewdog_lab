<template>
  <div>
    <h2>Favourites</h2>
    <ul>
      <li v-for="(fave, key) in favouriteBeers">{{ fave.name }}</li>
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
      if(!this.favouriteBeers.includes(beer)) {
        this.favouriteBeers.push(beer);
      }
    });
  }
};
</script>

<style>
</style>