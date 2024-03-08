<template>
  <div id="wxContainer">
    <div id="wxDiv" class="container">
      <Today />
      <Radar />
    </div>
  </div>
  <RetroScanFooter/>
</template>
<script>
import Today from './components/Today.vue'
import Radar from './components/Radar.vue'
import RetroScanFooter from './components/RetroScanFooter.vue'

export default {
  name: 'App',
  components: {
    Today,
    Radar,
    RetroScanFooter,
  }
}
</script>
<style scoped>
</style>