<template>
  <div id="app">
    <RestaurantCard/>
  </div>
</template>

<script>
import RestaurantCard from './components/RestaurantCard.vue'
export default {
  name: 'App',
  components: {
    RestaurantCard
  }
}
</script>

<style>
@import url('./style/reset.css');
@import url('./font/roboto.css');

#app {
  font-family: 'Roboto' , sans-serif;
}
</style>
