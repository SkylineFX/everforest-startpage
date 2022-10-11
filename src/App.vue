<script setup lang="ts">
  import Info from './components/Info.vue'
  import Search from './components/Search.vue'
  import Bookmarks from './components/Bookmarks.vue'
</script>

<template>
  <main>
    <div class="image">
      <img src="/image.png" alt="">
    </div>
    <div class="content">
      <Info/>
      <Search/>
      <Bookmarks/>
    </div>
  </main>
</template>

<style scoped>
  main {
    min-width: 70rem;
    height: 31rem;
    display: flex;
    justify-content: space-between;
    user-select: none;
  }

  .image {
    max-width: 31rem;
    height: 100%;
  }
  .image img {
    height: 100%;
    width: 100%;
    border-radius: 50px;
    user-select: none;
    pointer-events: none;
  }

  .content {
    width: 33rem;
    height: 100%;
    align-self: center;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
</style>