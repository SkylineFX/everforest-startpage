<script setup lang="ts">
  import Info from './components/Info.vue'
  import Search from './components/Search.vue'
  import Bookmarks from './components/Bookmarks.vue'
</script>

<template>
  <main>
    <div class="image">
      <img src="src/assets/succulent.png" alt="">
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
    min-width: 1130px;
    height: 500px;
    display: flex;
    justify-content: space-between;
    user-select: none;
  }

  .image {
    max-width: 500px;
    height: 500px;
  }
  .image img {
    height: 100%;
    width: 100%;
    border-radius: 50px;
  }

  .content {
    width: 530px;
    height: 100%;
    align-self: center;
  }
</style>
