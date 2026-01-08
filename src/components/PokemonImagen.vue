<template>
  <picture>
    <img :src="srcImagen" alt="No se puede renderizar la imagen" />
  </picture>
</template>

<script>
export default {
  props: {
    pokemonId: {
      type: Number,
      required: true
    }
  },
  computed: {
    srcImagen() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
    }
  }
}
</script>

<style scoped>
img {
  width: 250px;
  height: 250px;
}
</style>
