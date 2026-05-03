<script setup> 
import { ref } from 'vue'

const itemNovo = ref('') // coloquei para guardar o que o usuário digitar
const lista = ref([]) // coloquei para guardar a lista de itens

const adicionarItem = () => {
  if (itemNovo.value.trim() !== '') { // Coloquei para verificar se o campo não está vazio
    lista.value.push(itemNovo.value) // Adiciona o novo item à lista
    itemNovo.value = '' // Limpa o campo original
  }
}
</script>