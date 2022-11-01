<script setup lang="ts">
  import Info from './components/Info.vue'
  import Search from './components/Search.vue'
  import Bookmarks from './components/Bookmarks.vue'
</script>

<template>
  <main>
    <div class="image">
      <img src="/image-small.png" alt="">
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

  @media screen and (max-width: 1200px) {
    main {
      height: fit-content;
      width: 100vw;
      flex-direction: column-reverse;
      align-items: center;
      justify-content: center;
    }

    .image {
      display: none;
    }
    .content {
      height: fit-content;
      width: 90vw;
      justify-content: flex-start;
      gap: 5rem;
      margin: 5rem 0;
    }
  }

  @media screen and (max-width: 500px) {
    .content {
      gap: 3rem;
      margin: 3rem 0;
    }
  }
</style>