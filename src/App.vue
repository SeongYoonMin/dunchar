<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'
interface ILink {
  name: string
  path: string
}
const links = ref<ILink[]>([
  {
    name: 'HOME',
    path: '/'
  },
  {
    name: 'SEARCH',
    path: '/search'
  }
])
</script>

<template>
  <header class="headers">
    <h1>Dungeon & Fighter - 던캐</h1>
    <nav class="link">
      <RouterLink v-for="(items, index) in links" :key="index" :to="items.path">{{
        items.name
      }}</RouterLink>
    </nav>
  </header>
  <RouterView></RouterView>
  <footer class="footers">
    <a href="https://developers.neople.co.kr" target="_blank"><img src="./assets/images/powered_neople.png" alt="Neople 오픈 API"></a>
  </footer>
</template>

<style scoped lang="scss">
.headers {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 20px;
  padding: 8px 20px;
  .link {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
    a {
      text-decoration: none;
      color: #616161;
      font-size: 20px;
      font-weight: 500;
      transition: .3s all;
      &:hover {
        font-size: 24px;
        
      }
    }
  }
  h1 {
    font-size: 36px;
    font-weight: 500;
  }
}
.footers {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px 0;
}
</style>
