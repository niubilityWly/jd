<template>
  <div id="app">
    <shopHead></shopHead>
    <store></store>
  </div>
</template>

<script>
import shopHead from './components/shopHead.vue'
import store from './components/store.vue'

export default {
  name: 'app',
  components: {
    'store' : store,
    'shopHead' : shopHead 
  }
}
</script>

<style>
@import "./assets/main.css"
</style>
