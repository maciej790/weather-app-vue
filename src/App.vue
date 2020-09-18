<template>
  <div id="app">
      <transition-group name="fade">
        <SearchInput @handlechange="handlechange($event)"/>
        <Location :InputLocation = "InputValue" v-if="InputValue != ''"/>
        <Temperature :temperature = "roundTemperature" v-if="InputValue != '' && error != true"/>
        <Cloud v-if="InputValue != '' && error != true  && api_cloud_state == 'Clouds'"/>
        <Sun v-if="InputValue != '' && error != true && api_cloud_state == 'Clear'"/>
        <Rain v-if="InputValue != '' && error != true && api_cloud_state == 'Rain'"/>
          <div class="below">
            <Humidity :humandity = "api_humandity" v-if="InputValue != '' && error != true"/>
            <Wind :wind = "api_wind" v-if="InputValue != '' && error != true"/>
          </div>
      </transition-group>
  </div>
</template>

<script>

import SearchInput from './components/SearchInput.vue';
import Location from './components/Location.vue';
import Temperature from './components/Temperature';
import Cloud from './components/Cloud.vue';
import Sun from './components/Sun.vue';
import Rain from './components/Rain.vue';
import Humidity from './components/Humidity.vue';
import Wind from './components/Wind.vue';

//debounce
import debounce from 'lodash.debounce';

export default {
  name: 'App',
  components: {
    SearchInput,
    Location,
    Temperature,
    Cloud,
    Sun,
    Rain,
    Humidity,
    Wind

  },

  data(){
    return{
      InputValue: '',
      api_temperature: '',
      api_humandity : '',
      api_wind: '',
      api_cloud_state: '',
      error: false,
    }
  },

  
  computed: {
    roundTemperature: function(){
        return Math.round(this.api_temperature)
    }
  },


  


  methods: {
    handlechange: debounce(function(payload) {
    
      this.InputValue = payload

      //qpi query
      const API_KEY = '962e96c7edd5b917153804d1e003d0ff'
      const API = `https://api.openweathermap.org/data/2.5/weather?q=${this.InputValue}&appid=${API_KEY}&units=metric`

      fetch(API)
      .then(response => response.json())
             .then(data => {
            //variable from api
            this.api_temperature = data.main.temp
            this.api_humandity = data.main.humidity
            this.api_wind = data.wind.speed
            this.api_cloud_state = data.weather[0].main

            this.error = !true
            

          })
          .catch(error => 
              console.log(error),
              this.error = !false
          );

    
         
    }, 500),

    
  }





}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    text-align: center;
  }

  body{
    background: url('./assets/bcg.jpg');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    height: 100vh;
    font-family: 'Kufam', cursive;
    color: white;
  }

  #app{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .below{
    width: 100%;
    height: auto;
    margin-top: 50px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .fade-enter-active,
  .fade-leave-active {
    transition: all 0.7s ease;
  }
  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
    transform: translateY(20px);
  }

     @media only screen and (min-width: 600px) {
        .below{
          flex-direction: row;
        }

     }
</style>
