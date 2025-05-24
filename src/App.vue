<script setup>
import { reactive } from 'vue'

const ctfl = "https://bstqb.qa/img/selos/s-ctfl.png"
const ctal = "https://bstqb.qa/img/selos/s-ctal-ta.png"

const possuiCTFL = true
const possuiCTAL = false

const estado = reactive({
  contador: 0,
  email: ' ',
  saldo: 5000,
  transferindo: 0,
  nomes: ['João', 'Maria', 'José', 'Ana', 'Pedro'],
  nomeInserir: ''
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

function mostraSaldoFuturo(){
  const { saldo, transferindo } = estado
  return saldo - transferindo
}

function validaValorTransferencia(){
  const { saldo, transferindo } = estado
  return saldo >= transferindo
}

function cadastrarNome(){
  if (estado.nomeInserir.length >= 3) {
    estado.nomes.push(estado.nomeInserir)
  } else {
    alert('Nome deve ter pelo menos 3 caracteres')
  }
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

<hr>
Email: {{ estado.email }} <br>
<input type="email" @keyup="alteraEmail" />

<hr>

Saldo: {{ estado.saldo }} <br>
Transferindo: {{ estado.transferindo }} <br>
Saldo depois da transferência: {{ mostraSaldoFuturo() }} <br>
<input class="campo" :class="{ invalido: !validaValorTransferencia() }" @keyup="evento => estado.transferindo = evento.target.value" type="number" placeholder="Quantia a ser transferida" />
<button v-if="validaValorTransferencia()">Transferir</button>
<span v-else>Valor maior que o saldo</span>

<hr>

<ul>
  <li v-for="nome in estado.nomes">
    {{ nome }}
  </li>
</ul>
<input type="text" placeholder="Digite um nome" @keyup="evento => estado.nomeInserir = evento.target.value"/>
<button type="button" @click="cadastrarNome()">Cadastrar nome</button>

<h3 v-for="nome in estado.nomes"> {{ nome }} </h3>
</template>

<style scoped>

img {
  max-width: 300px;
}

.invalido {
  outline-color: red;
  border-color: red;
}

.campo {
  border: 2px solid black
}

</style>
