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
  <main style="padding: 20px; font-family: sans-serif; max-width: 500px; margin: auto;">
    <h1>🛒 Gerenciador de Compras</h1>

    <div class="input-group" style="margin-bottom: 20px;">
      <input 
        v-model="itemNovo" 
        @keyup.enter="adicionarItem" 
        placeholder="Digite um produto..."
        style="padding: 8px; width: 200px;"
      >
      <button @click="adicionarItem" style="padding: 8px 15px; cursor: pointer;">
        Adicionar
      </button>
    </div>

    <div v-if="lista.length > 0">
      <h3>Minha Cesta:</h3>
      <ul style="list-style: none; padding: 0;">
        <li v-for="(produto, index) in lista" :key="index" style="margin-bottom: 10px; border-bottom: 1px solid #eee; padding-bottom: 5px;">
          {{ produto }} 
          <button @click="removerProduto(index)" style="color: white; background: red; border: none; border-radius: 4px; padding: 5px 10px; margin-left: 15px; cursor: pointer;">
            Remover
          </button>
        </li>
      </ul>
      
      <p style="margin-top: 20px; font-weight: bold;">
        Total de itens na cesta: {{ lista.length }}
      </p>
    </div>
    
    <p v-else style="color: #666; font-style: italic;">
      Sua cesta está vazia! Adicione algo acima.
    </p>
  </main>
</template>

<style scoped>

</style>