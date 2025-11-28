<template>
  <div>
    <label for="id_nombre">Nombre: </label>
    <input v-model="nombre" type="text" id="id_nombre" />
    <p>{{ nombre }}</p>

    <label for="id_apellido">apellido: </label>
    <input v-model="apellido" type="text" id="id_apellido" />
    <!-- <p>{{ apellido }}</p> -->
    <button @click="imprimirNombre">Imprimir nombre</button>
    <button @click="agregarEstudiante">Agregar estudiante</button>

    <h1>{{ arreglo }}</h1>

    <ul>
      <li v-for="{ nombre, apellido } in arreglo" :key="nombre">
        {{ nombre }} - {{ apellido }}
      </li>
    </ul>
    <h2>Tabla</h2>
    <table v-if="arreglo.length > 0" border="1">
      <tr>
        <th>Nombre</th>
        <th>Apellido</th>
      </tr>
      <tr v-for="estudiante in arreglo" :key="estudiante.nombre">
        <td v-for="value in estudiante">{{ value }}</td>
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      nombre: null,
      apellido: null,
      arreglo: []
    }
  },
  methods: {
    imprimirNombre() {
      console.log(this.nombre)
    },
    agregarEstudiante() {
      const estu = {
        nombre: this.nombre,
        apellido: this.apellido
      }
      console.log(estu)

      this.arreglo.push(estu)
      console.log(this.arreglo)
      this.limpiarFormulario()
    },
    limpiarFormulario() {
      this.nombre = ''
      this.apellido = ''
    }
  }
}
</script>
<style></style>
