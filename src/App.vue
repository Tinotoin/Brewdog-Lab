<template lang="html">
  <div>
    <h1>Brewdog Beers</h1>
    <!-- <a href="https://api.punkapi.com/v2/beers?page=1&per_page=80">Page 1</a><br>
      <a href="https://api.punkapi.com/v2/beers?page=2&per_page=80">Page 2</a><br>
        <a href="https://api.punkapi.com/v2/beers?page=3&per_page=80">Page 3</a><br>
          <a href="https://api.punkapi.com/v2/beers?page=4&per_page=80">Page 4</a><br>
            <a href="https://api.punkapi.com/v2/beers?page=5&per_page=80">Page 5</a><br> -->
    <beer-filter-form :beers="beers" />
    <div class="main-container">
      <beer-detail style="text-align:right;" :beer="selectedBeer"></beer-detail>
      <beers-list :beers="beers"></beers-list>
      <!-- <beer-faves :beers-fave="beers-fave"></beer-faves> -->



    </div>
  </div>
</template>

<script>

import { eventBus } from './main.js';
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue'
import BeerFilterForm from './components/BeerFilterForm.vue'
// import BeerFaves from './components/BeerFaves.vue'

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      beersFave: []
    };
  },

  mounted(){
    fetch('https://api.punkapi.com/v2/beers?page=2&per_page=80')
    .then(result => result.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "beer-filter-form": BeerFilterForm,
    // "beers-fave": BeerFaves
  }
}

</script>





<style lang="css" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
