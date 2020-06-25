<template>
  <div class="beer">
    <img :src="beer.image_url" />
    <label class="favorite" for="checkbox">Mark as favourite</label>
    <input v-on:change="favourite" class="favorite" type="checkbox"></input>
    <h2>{{ beer.name }}</h2>
      <i>{{ beer.tagline }}</i>
      <p>{{ beer.description }}</p>
      <div class="clearfix"></div>
      <extrainfo :beer="beer"/>
    </div>
</template>

<script>
import extrainfo from './ExtraInfo.vue';
import { eventBus } from '../main.js';

export default {
  name: 'beer',
  props: [ 'beer' ],
  methods: {
    favourite(event) {
      eventBus.$emit('beer', this.beer);
    },
    extraInfo() {
      console.log('extra')
    }
  },
  components: {
    'extrainfo': extrainfo
    }
}
</script>

<style>
.beer {}

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
