<template>
  <main class="upload-container bg-zinc-700 rounded-md p-4 flex justify-center flex-col gap-6">
    <h1 class="text-zinc-100 text-xl font-medium">Salvar arquivos</h1>
    <input type="file" name="file" id="file" class="bg-zinc-600 rounded-xl text-zinc-100 p-4" />
    <input
      type="submit"
      value="Salvar"
      @click="sendFile"
      class="cursor-pointer bg-zinc-600 p-4 text-zinc-100 rounded-xl hover:brightness-110 transition-all"
    />
    <div v-if="url !== ''" class="text-zinc-100">
      <p @click="copyToClipboard">Clique para copiar a url!</p>
      <a class="text-zinc-400" href="{{ url }}">Clique para ir para a página!</a>
    </div>
  </main>
</template>

<script setup lang="js">
import { ref } from 'vue'

const url = ref('')

function copyToClipboard() {
  navigator.clipboard.writeText(url.value)
  alert('Copied to clipboard!')
}

async function sendFile(ev) {
  const file = ev.target.files[0]

  const form = new FormData()
  form.append('file', file)

  const response = await fetch('http://localhost:3333/', {
    method: 'POST',
    body: form
  })

  const data = await response.json()

  url.value = data.url
}
</script>
