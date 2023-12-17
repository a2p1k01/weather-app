<script setup>
  const props = defineProps(['weather'])
</script>

<template>
  <div id="weather_wrapper">
    <div class="weatherCard" v-if="weather !== null">
      <div class="currentTemp">
        <span class="temp">{{ weather["main"].temp }}&deg</span>
        <span class="location">{{ weather.name }}</span>
      </div>
      <div class="currentWeather">
        <div class="info">
          <span class="conditions">
            <img width="128px" height="128px" v-if="weather.weather[0].main.toLowerCase() === 'rain'" src="../assets/rain.png" alt="">
            <img width="128px" height="128px" v-if="weather.weather[0].main.toLowerCase() === 'clear'" src="../assets/sun.png" alt="">
            <img width="128px" height="128px" v-if="weather.weather[0].main.toLowerCase() === 'snow'" src="../assets/snow.png" alt="">
            <img width="128px" height="128px" v-if="weather.weather[0].main.toLowerCase() === 'clouds'" src="../assets/cloud.png" alt="">
          </span>
          <span class="rain">{{ weather["main"].humidity }} %</span>
          <span class="wind">{{ weather["wind"].speed }} MPS</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

@import url(https://cdnjs.cloudflare.com/ajax/libs/weather-icons/1.2/css/weather-icons.min.css);

#weather_wrapper{
  width: 400px;
  margin-left: 50%;
}

.weatherCard{
  width: 400px;
  height: 200px;
  font-family: "Comic Sans MS", serif;
  position: relative;
}

.currentTemp {
  width: 220px;
  height: 200px;
  background: rgb(41, 41, 41);
  position: absolute;
  top: 0;
  left: 0;
}

.currentWeather{
  width: 180px;
  height: 200px;
  background: rgb(237, 237, 237);
  margin: 0;
  position: absolute;
  top: 0;
  right: 0;
}

.temp{
  font-size: 74px;
  text-align: center;
  display: block;
  font-weight: 320;
  color: rgb(255, 255, 255);
  padding: 24px 0 0;
}

.location{
  color: rgb(255, 255, 255);
  text-align: center;
  text-transform: uppercase;
  font-weight: 700;
  font-size: 24px;
  display: block;
}

.info{
  width: 180px;
  height: 50px;
  position: absolute;
  bottom: 0;
  right: 0;
  background: rgb(42, 178, 234);
  font-weight: 700;
  color: rgb(255, 255, 255);
  text-align: center;
}

.rain {
  width: 50%;
  font-size: 15px;
  position: absolute;
  left: 10px;
  word-spacing: 60px;
  top: 3px;
}

.conditions{
  color: black;
  margin-top: -135px;
  font-family: weathericons,serif;
  font-size: 80px;
  display: block;
  text-align: center;
}

.rain::before{
  display: block;
  content: '\f04e';
  font-family: weathericons,serif;
  font-size: 40px;
  left: 6px;
  top: -4px;
  position: absolute;
}

.wind {
  width: 50%;
  font-size: 15px;
  right: -10px;
  position: absolute;
  word-spacing: 60px;
  top: 3px;
}

.wind::before{
  display: block;
  content: '\f050';
  font-family: weathericons,serif;
  font-size: 25px;
  left: -10px;
  position: absolute;
  top: 5px;
}

</style>