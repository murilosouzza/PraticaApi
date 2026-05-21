<template>
  <ListaDeUsuarios />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ListaDeUsuarios from './components/ListaDeUsuarios.vue'

export default defineComponent({
  components: { ListaDeUsuarios }
})
</script>