<template>

  <div v-if="isNormal" id="normal"></div>
  <div v-else id="vhsmode"></div>
  <div id="container">
    <Today />
    <div id="blankdiv"></div>

    <footer id="footer" class="text-white">
      <audio loop src="./music" ref="audioPlayer"></audio>
      <div id="retroDiv">


        <a href="#" @click="toggleDiv" class="text-white">retro mode > <img src="./components/icons/vhsmode.svg"
            alt="Retro mode" id="retroSvg">
        </a>

      </div>
    </footer>
  </div>
  <div id="blocker">
    <div id="blockerMessage">
<p class="display-4">This site was not designed for mobile devices.</p>
    <hr>
    <p class="lead">Please view on a personal computer or similar device.</p>
    </div>

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