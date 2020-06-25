<template>
  <div class="beer">
    <img :src="beer.image_url" />
    <h2>{{ beer.name }}</h2>
      <i>{{ beer.tagline }}</i>
      <p>{{ beer.description }}</p>
      <div class="clearfix"></div>
    </div>
</template>

<script>
export default {
  name: 'beer',
  props: [ 'beer' ]
}
</script>

<style>
.beer {
  border: 1px solid black;
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
