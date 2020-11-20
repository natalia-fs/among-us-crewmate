<template>
  <div id="app">
    <AmongUs/>
  </div>
</template>

<script>
import AmongUs from './components/AmongUs.vue'

export default {
  name: 'App',
  components: {
    AmongUs
  }
}
</script>

<style>
*, *:before, *:after{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
