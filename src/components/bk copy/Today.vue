<template>
  <div id="menu">
  <nav class="navbar">
    <div class="container-fluid">
      <a class="navbar-brand text-light">RetroScan Weather</a>
      <div class="dropdown">

        <button class="btn btn-info dropdown-toggle text-white" type="button" data-bs-toggle="dropdown"
          aria-expanded="false">
          Location
        </button>
        <ul class="dropdown-menu">
          <li><a class="dropdown-item" href="#" @click="changeCoords('EWX/30,97', 'Austin')">Austin</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('BOX/42,71', 'Boston')">Boston</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('TOP/41,87', 'Chicago')">Chicago</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('BOU/39,104', 'Denver')">Denver</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('EAX/39,94', 'Kansas City')">Kansas City</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('LOX/34,118', 'Los Angeles')">Los Angeles</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('LIX/30,9O', 'New Orleans')">New Orleans</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('OKX/40,73', 'New York')">New York</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('MTR/37,122', 'San Francisco')">San Francisco</a></li>
          <li><a class="dropdown-item" href="#" @click="changeCoords('SEW/47,122', 'Seattle')">Seattle</a></li>
        </ul>
      </div>
    </div>
  </nav>    
  </div>

  <div id="carouselWx" class="carousel slide carousel-fade" data-bs-ride="carousel">
    <div class="carousel-inner">
      <div v-for="wx in Forecast" :key="wx.number">
        <div class="carousel-item middle" :class="{ active: wx.number === 1 }" data-bs-interval="4000">
          <div class="row justify-content-md-center px-5">
            <div class="col-2 py-5">
              <img v-bind:src="wx.icon" v-bind:alt="wx.shortForcast" id="icon" class="align-middle">
            </div>
            <div class="col-7 py-2">
              <p class="lead text-center">{{ location }} | {{ wx.name }}</p>
              <hr>
              <p class="text-wrap">{{ wx.detailedForecast }}</p>
            </div>
            <div class="col-2"></div>
          </div>
        </div>
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselWx" data-bs-slide="prev"
      id="carButton">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselWx" data-bs-slide="next"
      id="carButton">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
</template>
<script>

import axios from 'axios';
export default {
  data() {
    return {
      Forecast: '',
      coords: 'EWX/30,97',
      location: 'Austin'
    }
  },
  methods: {
    changeCoords(newCoords, newLocation) {
      this.coords = newCoords;
      this.location = newLocation;
      this.GetForecast();
    },
    GetForecast() {
      //axios.get(this.coords).then(
      axios.get('https://api.weather.gov/gridpoints/' + this.coords + '/forecast').then(
        response => {
          //console.log(response.data.properties.periods[0].detailedForecast);
          this.Forecast = response.data.properties.periods;
        }
      ).catch(error => { console.log(error) })
    }
  },
  mounted() {
    this.GetForecast(); // Call the method on component mount
  },

};
</script>
<style>
</style>