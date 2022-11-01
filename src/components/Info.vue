<script setup lang="ts">
import { ref } from 'vue';
import Icon from './Icon.vue'

// Date and time
const currentDate = ref(new Date());
const formatDate = new Intl.DateTimeFormat("en-GB", { weekday: "long", day: "numeric", month: "long" }).format;

//init
const time = ref(currentDate.value.toLocaleTimeString('en-GB', { hour: '2-digit', minute: '2-digit', hour12: false }));
const date = ref(formatDate(currentDate.value));

setInterval(() => {
  currentDate.value = new Date();
  time.value = currentDate.value.toLocaleTimeString('en-GB', { hour: '2-digit', minute: '2-digit', hour12: false });
  date.value = formatDate(currentDate.value);
}, 1000 * 10);


// Weather
const refreshTime = 1000 * 60 * 30;

const success = (pos: any) => {

  const apiKey = '27b65c23de2d23cb0d71a8aafd988903'
  const apiLink = `https://api.openweathermap.org/data/2.5/weather?lat=${pos.coords.latitude}&lon=${pos.coords.longitude}&units=metric&appid=${apiKey}`
  getWeather(apiLink);

  setInterval(() => {
    getWeather(apiLink)
  }, refreshTime)
}

const error = (err: any) => {
  console.warn(`ERROR(${err.code}): ${err.message}`);
}

const options = {
  enableHighAccuracy: true,
  timeout: 5000,
  maximumAge: 0
};

const getWeather = async (apiLink: string) => {
  let weatherObj = await fetch(apiLink);
  let weatherData = JSON.parse(await weatherObj.text());
  temp.value = Math.floor(weatherData.main.temp) + '°' + 'C';
  desc.value = weatherData.weather[0].description;
  icon.value = setIcon(weatherData.weather[0].icon);
}

const setIcon = (code: string) => {
  if(code == '01d') return 'Sun'
  if(code == '01n') return 'Moon'
  if(code.includes('02')) return 'CloudSun'
  if(code.includes('03')) return 'Cloud'
  if(code.includes('04')) return 'Cloudy'
  if(code.includes('09') || code.includes('10')) return 'CloudRainWind'
  if(code.includes('11')) return 'CloudLightning'
  if(code.includes('13')) return 'Snowflake'
  if(code.includes('50')) return 'CloudFog'
}

//init
const temp = ref();
const desc = ref(); 
const icon = ref();

navigator.geolocation.getCurrentPosition(success, error, options);
</script>

<template>
  <div class="info">
    <div class="datetime-container">
      <div class="time">{{time}}</div>
      <div class="date">{{date}}</div>
    </div>
    <div class="weather-container">
      <div class="weather">
        <Icon :name="icon" size="35" style="margin-bottom: 7px"/>
        <div class="degrees">{{temp}}</div>
      </div>
      <div class="description">{{desc}}</div>
    </div>
  </div>
</template>

<style scoped>
.info {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.datetime-container, .weather-container {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.time {
  font-size: 48px;
  height: 75%;
}

.date {
  height: 25%;
}

.weather {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 10px;
  height: 75%;
}

.degrees {
  width: fit-content;
  height: 40px;
  font-size: 36px;
  margin-bottom: 7px;
}

.description {
  height: 25%;
  text-align: right;
}

@media screen and (max-width: 500px) {
    .time {
      font-size: 36px;
    }
    .degrees {
      font-size: 32px;
    }
  }
</style>