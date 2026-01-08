<template>
  <div class="container">
    <PokemonImagen :pokemonId="8" />
    <PokemonOpciones />
  </div>
</template>
<script>
import PokemonImagen from '@/components/PokemonImagen.vue'
import PokemonOpciones from '@/components/PokemonOpciones.vue'
export default {
  components: {
    PokemonImagen,
    PokemonOpciones
  }
}
</script>
<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 20px;
}
</style>
