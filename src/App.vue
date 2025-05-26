<script setup>
  import { reactive, ref, watch } from 'vue'
  import Header from './components/Header.vue'
  import Form from './components/Form.vue'

  const estado = reactive({
    resultado: 0,
    operacoes: ['Adição', 'Subtração', 'Multiplicação', 'Divisão'],
  })

  const input1 = ref(0)
  const input2 = ref(0)
  const filtro = ref('Adição')


  watch([input1, input2, filtro], () => {
    switch (filtro.value) {
      case 'Adição':
        estado.resultado = Number(input1.value) + Number(input2.value)
        break
      case 'Subtração':
        estado.resultado = Number(input1.value) - Number(input2.value)
        break
      case 'Multiplicação':
        estado.resultado = Number(input1.value) * Number(input2.value)
        break
      case 'Divisão':
        estado.resultado = input2.value != 0 ? Number(input1.value) / Number(input2.value) : 'Divisão por zero'
        break
      default:
        estado.resultado = 0
    }
  }, { immediate: true })
</script>

<template>
  <div class="container">
    <Header :resultado="estado.resultado" />
    <Form
      :getOperacao="getOperacao"
      :estado="estado"
      v-model:input1="input1"
      v-model:input2="input2"
      v-model:filtro="filtro"
    />
  </div>
</template>

<style scoped>
  .container {
    background-color: cadetblue;
  }
</style>