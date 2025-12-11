<template>
  <img
    v-if="!imagen"
    src="https://yesno.wtf/assets/yes/5-64c2804cc48057b94fd0b3eaf323d92c.gif"
    alt=""
  />
  <img v-if="imagen" :src="imagen" alt="" />
  <div class="pregunta-container">
    <h1>Pregunta</h1>
    <input
      type="text"
      placeholder="Haz una pregunta"
      @keypress.enter="llamadaAPI"
    />
    <p>Recuerda terminar con el signo de interrogación (?)</p>
    <h2>Sere millonario</h2>
    <h1 v-if="!respuesta">Yes, NO</h1>
    <p v-if="respuesta">{{ respuesta }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return { imagen: null, respuesta: null }
  },
  methods: {
    llamadaAPI() {
      fetch('https://yesno.wtf/api')
        .then((response) => response.json())
        .then((data) => {
          console.log(data)

          this.respuesta = data.answer
          this.imagen = data.image
        })
        .catch((error) => {
          console.error('Error:', error)
        })
    }
  }
}
</script>

<style scoped>
img {
  position: fixed;
  width: 100%;
  height: 100dvh;
  top: 0;
  left: 0;
}
.pregunta-container {
  position: relative;
  background-color: rgba(255, 255, 255, 0.5);
  padding: 8px;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  font-size: 18px;
}
input {
  padding: 8px 12px;
  font-size: 16px;
  border: none;
  border-radius: 14px;
  width: 300px;
}
input:focus {
  outline: none;
}
</style>
