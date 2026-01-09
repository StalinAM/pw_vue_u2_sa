<template>
  <div class="container">
    <PokemonImagen :pokemonId="pokemonGanador" />
    <PokemonOpciones
      @seleccionado="evaluarGanador($event)"
      :listaPokemons="pokemonArr"
    />
    <p v-if="mensaje">{{ mensaje }}</p>
  </div>
</template>
<script>
import PokemonImagen from '@/components/PokemonImagen.vue'
import PokemonOpciones from '@/components/PokemonOpciones.vue'
import {
  obtenerVectorPokemonesFacade,
  obtenerAleatorioFacade
} from '@/clients/PokemonClient.js'
export default {
  components: {
    PokemonImagen,
    PokemonOpciones
  },
  data() {
    return {
      pokemonArr: [],
      pokemonGanador: null,
      mensaje: null
    }
  },
  mounted() {
    this.iniciarJuego()
  },
  methods: {
    async iniciarJuego() {
      this.pokemonArr = await obtenerVectorPokemonesFacade()
      const idAleatorio = obtenerAleatorioFacade(0, 3)
      this.pokemonGanador = this.pokemonArr[idAleatorio].id

      this.mensaje = null
    },
    evaluarGanador(idSeleccionado) {
      if (idSeleccionado !== this.pokemonGanador) {
        this.mensaje = '¡Has perdido! Inténtalo de nuevo.'
      } else {
        this.mensaje = '¡Has ganado! ¡Felicidades!'
      }
    }
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
p {
  font-size: 24px;
  font-weight: bold;
  border: 1px solid red;
  padding: 8px 16px;
  border-radius: 8px;
}
</style>
