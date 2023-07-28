<template>
  <div id="app">
    <home />
  </div>
</template>

<script>
import Home from './page/home.vue';

export default {
  name: 'App',
  components: {
      Home
  }
}
</script>

<style>
@import url('./style/reset.css');
@import url('./font/roboto.css');

#app {
  font-family: 'Roboto' , sans-serif;
  padding: 0px 20px;
}
</style>
