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

    <hr />
    <label for="id_nombre_1">Nombre:</label>
    <input v-model="nombre" type="text" id="id_nombre_1" />
    <label for="id_apellido_1">Apellido:</label>
    <input
      v-model="apellido"
      v-on:keypress.enter="agregarEstudiante1"
      type="text"
      id="id_apellido_1"
    />
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
    agregarEstudiante1(event) {
      console.log('evento')

      if (event.charCode !== 13) return
      const estu = {
        nombre: this.nombre,
        apellido: this.apellido
      }
      this.arreglo.push(estu)
      this.limpiarFormulario()
      console.log('Enter presionado')

      console.log('Se agrego estudiante 1')
      console.log(event)

      console.log(event.charCode)
    },
    limpiarFormulario() {
      this.nombre = ''
      this.apellido = ''
    }
  }
}
</script>
<style></style>
