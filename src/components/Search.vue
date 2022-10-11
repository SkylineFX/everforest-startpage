<script setup lang="ts">
  import { ref } from 'vue'
  import Icon from './Icon.vue'

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
    width: 100%;
    height: 3rem;
    position: relative;
    border-bottom: 2px solid var(--fg);
    display: flex;
    align-items: center;
  }

  input {
    width: calc(100% - 30px);
    height: inherit;
    border: none;
    background: #2b3339;
    outline: none;
    caret-color: var(--fg);
    font-size: 24px;
    color: var(--fg);
    line-height: 2;
    position: absolute;
    bottom: 0;
    left: 30px;
    z-index: 1;
  }
  
.input-container::before {
    content: ">";
    color: var(--fg);
    position: absolute;
    left: 0px;
    bottom: 0px;
    font-size: 30px;
    z-index: 2;
  }
</style>