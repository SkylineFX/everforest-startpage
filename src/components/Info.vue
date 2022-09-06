<script setup lang="ts">
  import { ref } from 'vue';
  import Icon from './Icon.vue'

  // Date and time
  const currentDate = ref(new Date());
  const formatDate = new Intl.DateTimeFormat("en-GB", { weekday: "long", day: "numeric", month: "long" }).format;

  const time = ref(currentDate.value.toLocaleTimeString('en-GB', {hour: '2-digit', minute:'2-digit', hour12:false}));
  const date = ref(formatDate(currentDate.value));

  setInterval(() => {
    currentDate.value = new Date();
    time.value = currentDate.value.toLocaleTimeString('en-GB', {hour: '2-digit', minute:'2-digit', hour12:false});
    date.value = formatDate(currentDate.value);
  }, 10000);

  // Weather
  //TODO
</script>

<template>
  <div class="info">
    <div class="datetime-container">
      <div class="time">{{time}}</div>
      <div class="date">{{date}}</div>
    </div>
    <div class="weather-container">
      <Icon name="Cloud" size="50"/>
      <div class="weather">
        <p>27°C</p>
        <span>75%</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.info {
    width: 530px;
    display: flex;
    justify-content: space-between;
  }

  .time {
    font-size: 48px;
  }

  .weather-container {
    display: flex;
    align-items: center;
    gap: 15px;
  }

  .weather {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .weather p {
    font-size: 22px;
    border-bottom: 2px solid #d3c6aa;
    margin-bottom: 3px;
  }

  .weather span {
    font-size: 22px;
  }
</style>