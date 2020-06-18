<template lang="html">
  <div>
    <div class="sub-container">

      <div v-if='beer'>
        <h3>{{beer.name}}</h3>
        <h4>{{beer.first_brewed}}</h4>
        <p><b>Strength:</b> {{beer.abv}}%</p>
        <p><b>Tasting Notes:</b> {{beer.description}}</p>
        <img class="med-image" :src="beer.image_url"/>

        <ul>
          <li v-for="(beer, index) in beers" :key="index">
            <span>{{beer.name}}</span>
            <!-- <span v-if="beerFave.includes(beer)? 'Favourite' : ''">Favourite</span> -->
            <button v-on:click="addToFavourites(index)">Favourite</button>
          </li>
        </ul>

      </div>
    </div>
  </div>

</template>

<script>

import {eventBus} from '../main.js'

export default {

  name: 'beer-detail',
  props: ['beer'],

  methods: {
    addToFavourites(){
    eventBus.$emit('beer-selected', this.beer)
    },
  },
};


 </script>

<style lang="css" scoped>



.med-image {
  height: 200px;
}

</style>
