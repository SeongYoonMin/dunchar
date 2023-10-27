<script setup lang="ts">
import { useRoute } from 'vue-router';

const route = useRoute();
const resultId = route.params.charId;
</script>

<template>
  <section>
    <p v-if="resultId">{{ resultId }}</p>
  </section>
</template>

<style lang="scss" scoped></style>
