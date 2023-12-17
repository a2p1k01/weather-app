<script>
import axios from 'axios';
import WeatherCard from "@/components/WeatherCard.vue";

const api_key = "PUT YOUR KEY HERE"

export default {
  components: {WeatherCard},
  data() {
    return {
      city: "",
      weather: null
    }
  },
  methods: {
    async getWeather(city) {
      try {
        await axios.get(
          `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${api_key}&units=metric`
        ).then((response) => {
          this.weather = response.data;
        });
        console.log(this.weather);
      } catch (error) {
        console.log(error);
      }
      this.city = "";
    },
  }
};
</script>


<template>
  <div id="app parent">
    <WeatherCard :weather="weather"/>
    <br>
    <div class="block">
      <input class="input block center" @keyup.enter="getWeather(city)" type="text" v-model="city">
      <button class="btn block center" @click="getWeather(city)">Get weather</button>
    </div>
  </div>
</template>


<style scoped>
    
#parent {
  text-align:center;
  background-color:blue;
  height:400px;
  width:600px;
}

br {
  margin-top: 5px;
}

.block {
  margin-left: 50%;
  height:100px;
  width:200px;

}
.center {
  margin-left: 50%;
  margin:auto;
}

.input {
  font-size: 14px;
  margin-top: 5px;
  margin-left: 50%;
  border-radius: 6px;
  line-height: 1.5;
  padding: 5px 10px;
  transition: box-shadow 100ms ease-in, border 100ms ease-in, background-color 100ms ease-in;
  border: 2px solid #dee1e2;
  color: rgb(14, 14, 16);
  background: #dee1e2;
  display: block;
  height: 36px;
}

.btn {
  margin-left: 50%;
  margin-top: 5px;
  height: 40px;
  width: 200px;
  background-color: #0A66C2;
  font-family: -apple-system, system-ui, system-ui, "Segoe UI", Roboto, "Helvetica Neue", "Fira Sans", Ubuntu, Oxygen, "Oxygen Sans", Cantarell, "Droid Sans", "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Lucida Grande", Helvetica, Arial, sans-serif;
  font-size: 16px;
  font-weight: 600;
  border: 0;
  color: white;
  border-radius: 5px;
}
</style>