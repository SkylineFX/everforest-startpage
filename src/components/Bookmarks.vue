<script setup lang="ts">
  import Icon from './Icon.vue'
  import {ref} from 'vue'

  const bookmarks = ref([
    {name: 'Github', link: 'github.com', icon: 'Github'},
    {name: 'Youtube', link: 'youtube.com', icon: 'Youtube'},
    {name: 'Gmail', link: 'gmail.com', icon: 'Mail'},
    {name: 'Spotify', link: 'spotify.com', icon: 'Music'},
    {name: 'Whatsapp', link: 'web.whatsapp.com', icon: 'Send'},
    {name: 'Monkeytype', link: 'monkeytype.com', icon: 'Type'},
  ]);

  const openBookmark = (bookmark: any) => {
    window.open('https://' + bookmark.link, '_blank');
  }
</script>

<template>
<div class="bookmark-container">
  <div class="bookmark" v-for="bookmark in bookmarks" :key="bookmark.name" @click="openBookmark(bookmark)">
    <Icon :name="bookmark.icon" size="30"/>
    <div class="text">
      <p class="name">{{bookmark.name}}</p>
      <span class="link">{{bookmark.link}}</span>
    </div>
  </div>
</div>
</template>

<style scoped>
  .bookmark-container {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(3, 3rem);
    grid-gap: 40px;
  }

  .bookmark {
    justify-self: left;
    height: 3rem;
    width: 100%;
    display: flex;
    align-items: center;
    gap: 20px;
    cursor: pointer;
  }

  .link {
    color: var(--accent);
  }
</style>