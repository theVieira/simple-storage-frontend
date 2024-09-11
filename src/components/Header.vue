<template>
  <header class="w flex items-center justify-center py-3 bg-zinc-600 gap-6 text-zinc-200">
    <RouterLink to="/" class="hover:brightness-125">Listar arquivos</RouterLink>
    <RouterLink to="/upload" class="hover:brightness-125">Salvar arquivos</RouterLink>
  </header>
</template>

<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>
