<template>
  <div class="opciones-container">
    <ul>
      <li>Pokemon 1</li>
      <li>Pokemon 2</li>
      <li>Pokemon 3</li>
      <li>Pokemon 4</li>
    </ul>
  </div>
</template>
<script>
import { consumirAPIFacade } from '@/clients/PokemonClient.js'
export default {
  data() {
    return {
      nombresPokemones: []
    }
  },
  props: {
    pokemonId: {
      type: Number,
      required: true
    }
  }
}
</script>
<style>
ul {
  list-style-type: none;
  display: flex;
  gap: 10px;
}
li {
  background-color: #f0f0f0;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
  border: 1px solid;
  transition: transform 0.2s;
}
li:hover {
  transform: scale(1.1);
}
li:active {
  transform: scale(0.95);
}
</style>
