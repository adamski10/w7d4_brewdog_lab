<template>
  <div>
    <input v-if="!clicked" v-on:click="extraInfo" type="submit" value="More info..." />
    <div v-if="clicked">
      <p>ABV: {{beer.abv}} %</p>
      <p>Brewers Tips: {{beer.brewers_tips}}</p>

      </div>
  </div>
</template>

<script>
export default {
  name: "extrainfo",
  props: ['beer'],
  data() {
    return { 
      clicked: false
    };
  },
  methods: {
    extraInfo() {
      this.clicked = true;
    }
  }
};
</script>

<style>
</style>
