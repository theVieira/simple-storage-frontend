<script setup lang="ts">
import { RouterView } from 'vue-router'
import Header from './components/Header.vue'
</script>

<template>
  <main class="min-h-screen bg-zinc-800 flex flex-col">
    <Header class="fixed top-0 w-screen" />
    <RouterView />
  </main>
</template>

<style scoped></style>
