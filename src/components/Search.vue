<script setup lang="ts">
  import { ref } from 'vue'

  const query = ref();
  const search = (event: any) => {
    if(event.key == "Enter" && query)
    {
      if(query.value.includes('.')) window.open('https://' + query.value);
      else window.open('https://duckduckgo.com/?q=' + query.value.replace(/ /g, '+'), '_blank');
      query.value = '';
    }
  }
</script>

<template>
<div class="input-container">
  <input type="text" autofocus autocomplete="off" placeholder="search..." v-model="query" @keyup="search">
</div>
</template>

<style scoped>
  .input-container {
    width: 530px;
    height: fit-content;
    margin: 100px 0 70px 0;
    position: relative;
    border-bottom: 2px solid #d3c6aa;
  }

  input {
    width: calc(100% - 30px);
    appearance: none;
    border: none;
    background: #2b3339;
    outline: none;
    caret-color: #d3c6aa;
    font-size: 24px;
    color: #d3c6aa;
    line-height: 2;
    position: absolute;
    bottom: 0;
    left: 30px;
    z-index: 1;
  }
  
  .input-container::before {
    content: ">";
    color: #d3c6aa;
    position: absolute;
    left: 0px;
    bottom: 0px;
    font-size: 35px;
    z-index: 2;
  }
</style>