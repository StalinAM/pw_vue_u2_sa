<template>
  <div>
    <h1>{{ titulo }}</h1>
    <h1>{{ tit }}</h1>
    <p>{{ numero }} <sup>2</sup> = {{ calculaCuadrado }}</p>
    <p>{{ numero }} <sup>3</sup> = {{ obtenerCubo() }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calculaCuadrado }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calculaCubo }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calculaCuadrado }}</p>

    <div>
      <button v-on:click="incrementar">+ 1</button>
      <button @click="decrementar">- 1</button>
      <button v-show="mostrar">Mostrar</button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      numero: this.inicio,
      titulo: 'Contador'
    }
  },
  methods: {
    //en propiedades reactivas la buena práctica es usar this
    obtenerCuadrado() {
      console.log('Entro a obtener cuadrado')
      return this.numero * this.numero
    },
    obtenerCubo() {
      console.log('Entro a obtener cubo')
      return this.numero * this.numero * this.numero
    },
    incrementar() {
      console.log(this.tit)

      this.numero++
    },
    decrementar() {
      this.numero--
    }
  },
  computed: {
    calculaCuadrado() {
      console.log('Entro a propiedad computada')

      return this.numero * this.numero
    },
    calculaCubo() {
      console.log('Entro a propiedad computada')
      return this.numero * this.numero * this.numero
    }
  },
  // props: ['tit', 'inicio', 'mostrar'] <-- declaracion basica
  props: {
    tit: String,
    inicio: {
      type: Number,
      default: 99,
      validator(value) {
        return value > 10
      }
    },
    mostrar: Boolean
  }
  /* String, Number, Boolean, Array, Object, Function, BigInt */
}
</script>
<style></style>
