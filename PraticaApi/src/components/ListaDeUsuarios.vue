<template>
  <div>
    <p v-if="carregando">Carregando...</p>

    <ul v-else>
      <li v-for="usuario in usuarios" :key="usuario.id">
        {{ usuario.name }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import axios from 'axios'

export default defineComponent({
  name: 'ListaDeUsuarios',

  data() {
    return {
      usuarios: [] as { id: number; name: string }[],
      carregando: true
    }
  },

  async created() {
    console.log('created: componente criado, buscando usuários...')

    const resposta = await axios.get('https://jsonplaceholder.typicode.com/users')
    this.usuarios = resposta.data
    this.carregando = false
  },

  mounted() {
    console.log('mounted: componente inserido no DOM')
  },

  unmounted() {
    console.log('unmounted: componente removido do DOM')
  },

  updated() {
    console.log('updated: componente atualizado (lista chegou)')
  }
})
</script>