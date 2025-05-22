<script setup>
import { reactive } from 'vue'

const ctfl = "https://bstqb.qa/img/selos/s-ctfl.png"
const ctal = "https://bstqb.qa/img/selos/s-ctal-ta.png"

const possuiCTFL = true
const possuiCTAL = false

const estado = reactive({
  contador: 0
})

function incrementar(){
  estado.contador++
}

function decrementar(){
  estado.contador--
}

function alteraEmail(evento){
  estado.email = evento.target.value
}

</script>

<template>
  <h1>Calculadora Aritmética</h1>
  <img v-if="possuiCTFL" :src="ctfl" alt="CTFL" />
  <img v-else-if="possuiCTAL" :src="ctal" alt="CTAL" />
  <h2 v-else>Não possui certificação</h2>

{{  estado.contador  }}
<button type="button" @click="incrementar">+</button>
<button type="button" @click="decrementar">-</button>

<hr />
{{ estado.email }}
<input type="email" @keyup="alteraEmail" />

</template>

<style scoped>

img {
  max-width: 300px;
}

</style>
