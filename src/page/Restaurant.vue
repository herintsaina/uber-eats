<template>
  <p>{{ $route.params.name }}</p>
</template>

<script>
import BDD from '../BDD.js'
import { onMounted } from 'vue'

export default {
    name: 'Restaurant',
    setup () {
      onMounted(() => {
        console.log(BDD);
      })
    }
}
</script>

<style>

</style>