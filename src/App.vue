<template>
  <div v-if="isNormal" id="normal"></div>
  <div v-else id="vhsmode"></div>
  <div id="container">
    <Today />
    <div id="blankdiv"></div>
 
  <footer id="footer" class="text-white">
    <audio loop src="./music.mp3" ref="audioPlayer"></audio>
    <div id="retroDiv">
      
      
      <a href="#" @click="toggleDiv" class="text-white">retro mode > <img src="./components/icons/vhsmode.svg" alt="Retro mode" id="retroSvg"> 
      </a>
      
    </div>
  </footer>    
  </div>

</template>
<script>

import Today from './components/Today.vue'

export default {

  data() {
    return {
      isNormal: true
    };
  },
  methods: {
    toggleDiv() {
      this.isNormal = !this.isNormal;
      const audioPlayer = this.$refs.audioPlayer;
      if (this.isNormal) {
        audioPlayer.pause();
      } else {
        audioPlayer.play();
      }
    }
  },

  name: 'App',
  components: {
    Today
  }

}


</script>

<style scoped></style>