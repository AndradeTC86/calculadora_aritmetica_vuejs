<script setup>

const ctfl = "https://bstqb.qa/img/selos/s-ctfl.png"
const ctal = "https://bstqb.qa/img/selos/s-ctal-ta.png"

const possuiCTFL = true
const possuiCTAL = false

</script>

<template>
  <h1>Calculadora Aritmética</h1>
  <img v-if="possuiCTFL" :src="ctfl" alt="CTFL" />
  <img v-else-if="possuiCTAL" :src="ctal" alt="CTAL" />
  <h2 v-else>Não possui certificação</h2>
</template>

<style scoped>

img {
  max-width: 300px;
}

</style>
