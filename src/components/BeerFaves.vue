<template lang="html">
  <ul>
    <li v-for="(beer, index) in beers" :key="index">
      <span>{{beer.name}}</span>
      <!-- <span v-if="faveBeers.includes(beer)? 'Favourite' : ''">Favourite</span> -->
      <button v-on:click="makeFavourite(index)">Favourite</button>
    </li>
  </ul>
</template>

<script>

import {eventBus} from '../main.js'
import BeerDetail from './components/BeerDetail.vue'

export default {
  name: 'beers-fave',
  props: ['beers'],
  methods: {
    addFavourite(){
      eventBus.$emit('beers-fave', this.beerFaves)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
