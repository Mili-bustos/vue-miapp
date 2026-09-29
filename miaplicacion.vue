<template>
  <div class="contenedor">
    <h1 v-bind:title="titulo">{{ titulo }}</h1>

    <input
      type="text"
      v-model="nombre"
      placeholder="Escribí tu nombre"
    />

    <h2>{{ nombre }}</h2>

    <button v-on:click="mostrar = !mostrar">
      {{ mostrar ? "Ocultar" : "Mostrar" }}
    </button>

    <p v-if="mostrar">
      Bienvenido {{ nombre }}
    </p>

    <h3>Lista de frutas</h3>

    <input
      type="text"
      v-model="nuevaFruta"
      placeholder="Ingresá una fruta"
    />

    <button v-on:click="agregarFruta">
      Agregar
    </button>

    <ul>
      <li v-for="(fruta, i) in frutas" :key="i">
        {{ fruta }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from "vue"

const titulo = ref("Aplicación de Vue")
const nombre = ref("")
const mostrar = ref(true)

const nuevaFruta = ref("")
const frutas = ref([])

function agregarFruta() {
  if (nuevaFruta.value != "") {
    frutas.value.push(nuevaFruta.value)
    nuevaFruta.value = ""
  }
}
</script>

<style scoped>
.contenedor {
  width: 400px;
  margin: 40px auto;
  padding: 20px;
  border-radius: 10px;
  background: #f76363;
  font-family: Arial, sans-serif;
  text-align: center;
}

input {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
}

button {
  padding: 10px 20px;
  background: #6c63ff;
  color: rgb(255, 255, 255);
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

ul {
  text-align: left;
  margin-top: 15px;
}
</style>
