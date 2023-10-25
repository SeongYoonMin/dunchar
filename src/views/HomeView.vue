<script setup lang="ts">
console.log(import.meta.env);
</script>

<template>
  <main class="home">
    <picture class="logo"><img src="../assets/images/logos.png" alt=""></picture>
    <h1 class="title">던파 캐릭터 검색</h1>
    <div class="info">
      <p>이곳은 네오플의 던파 OpenAPI를 이용해 만들어진 사이트입니다.</p>
    </div>
  </main>
</template>
<style scoped lang="scss">
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
  padding: 40px 0;
  .logo {
    max-width: 400px;
    display: block;
  }
  .title {
    font-size: 40px;
    font-weight: 500;
  }
}
</style>
