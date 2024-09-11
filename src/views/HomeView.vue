<template>
  <main class="home-container h-screen flex items-center justify-center gap-6">
    <div
      v-for="file in files"
      :key="file.id"
      class="file text-zinc-200 rounded-3xl bg-zinc-900 p-8"
    >
      <p>Nome: {{ file.filename }}</p>
      <p>
        URL:
        <a :href="file.url" target="_blank" class="text-zinc-400 hover:text-zinc-200 transition-all"
          >Clique para abrir</a
        >
      </p>
    </div>
  </main>
</template>

<script setup lang="ts">
import { onBeforeMount, ref } from 'vue'

const files = ref()

onBeforeMount(async () => {
  const res = await fetch('http://localhost:3333')

  const data = await res.json()

  files.value = data
})
</script>
