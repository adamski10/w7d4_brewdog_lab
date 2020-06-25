<template>
  <div class="beer">
    <img :src="beer.image_url" />
    <label class="favorite" for="checkbox">Mark as favourite</label>
    <h2>{{ beer.name }}</h2>
    <input v-on:change="favourite" class="favorite" type="checkbox"></input>
      <i>{{ beer.tagline }}</i>
      <p>{{ beer.description }}</p>
      <div class="clearfix"></div>
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'beer',
  props: [ 'beer' ],
  methods: {
    favourite(event) {
      eventBus.$emit('beer', this.beer);
    }
  }
}
</script>

<style>
.beer {
  border: 1px solid black;
}


.favorite {
  float: right;
}
img {
  height: 150px;
  float: left;
}

.clearfix::after {
  content: "";
  clear: both;
  display: table;
}
</style>
