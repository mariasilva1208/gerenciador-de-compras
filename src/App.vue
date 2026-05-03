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

const removerProduto = (index) => {
  lista.value.splice(index, 1)
}
</script>

<template>
  <main style="padding: 20px; font-family: sans-serif;">
    <h1> Gerenciador de Compras</h1>

    <div class="input-group">
      <input 
        v-model="itemNovo" 
        @keyup.enter="adicionarItem" 
        placeholder="Digite um produto..."
      >
      <button @click="adicionarItem">Adicionar</button>
    </div>

    <div v-if="lista.length > 0">
      <h3>Minha Cesta:</h3>
      <ul>
        <li v-for="(produto, index) in lista" :key="index">
          {{ produto }} 
          <button @click="removerProduto(index)" style="color: red; margin-left: 10px;">
            Remover
          </button>
        </li>
      </ul>
      <p>Quantidade total: <strong>{{ lista.length }}</strong></p>
    </div>
    
    <p v-else>Sua cesta está vazia!</p>
  </main>
</template>