<script setup>
import { ref } from 'vue'
const itemNovo = ref('')
const lista = ref([])

const adicionarItem = () => {
  if (itemNovo.value.trim() !== '') {
    lista.value.push(itemNovo.value)
    itemNovo.value = ''
  }
}
</script>
<template>
  <main>
    <h1> Gerenciador de Compras</h1>
    
    <input v-model="itemNovo" @keyup.enter="adicionarItem" placeholder="Produto...">
    <button @click="adicionarItem">Adicionar</button>
    
    <ul>
      <li v-for="(item, index) in lista" :key="index">{{ item }}</li>
    </ul>
  </main>
  </template>