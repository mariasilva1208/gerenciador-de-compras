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
    <footer class="rodape">
      <p>Desenvolvido com cansaço por <strong>Maria Eduarda Patu Ângelo da Silva</strong></p>
      <p>© 2026 </p>
    </footer>
  </main>
</template>

<style scoped>


main {
  max-width: 450px;
  margin: 40px auto;
  padding: 25px;
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  text-align: center;
  color: #333;
}

h1 {
  color: #42b883; 
  margin-bottom: 25px;
}


input {
  padding: 10px;
  border: 2px solid #ddd;
  border-radius: 6px;
  width: 60%;
  margin-right: 10px;
  outline: none;
  transition: border-color 0.3s;
}

input:focus {
  border-color: #42b883;
}


button {
  padding: 10px 15px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
  transition: opacity 0.2s;
}

button:hover {
  opacity: 0.8;
}


.input-group button {
  background-color: #42b883;
  color: white;
}


li button {
  background-color: #ff4d4d;
  color: white;
  padding: 5px 10px;
  font-size: 0.8rem;
}

/* Lista */
ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

li {
  background: #f9f9f9;
  margin-bottom: 10px;
  padding: 12px;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}


.contador {
  margin-top: 20px;
  font-size: 1.1rem;
  color: #666;
}

.vazia {
  color: #999;
  font-style: italic;
  margin-top: 20px;
}
.rodape {
  margin-top: 40px;
  padding-top: 20px;
  border-top: 1px solid #eee;
  font-size: 0.9rem;
  color: #888;
}

.rodape strong {
  color: #000704; 
}
</style>