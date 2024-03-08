<template>
  <div id="vhsmode"></div>
  <div id="container">
    
    <Today />
  </div>

</template>

<script>

import Today from './components/Today.vue'

export default {
  name: 'App',
  components: {
    Today,
  }
}
</script>

<style scoped></style>