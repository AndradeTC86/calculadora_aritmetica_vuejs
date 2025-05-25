<script setup>

  import { reactive } from 'vue'
  import Header from './components/Header.vue'
  import Form from './components/Form.vue'
  import TaskList from './components/TaskList.vue'

  const estado = reactive({
    tarefaTemp: '',
    filtro: 'todas',
    tarefas : [
      {
        titulo: 'Estudar ES6',
        finalizada: false
      },
      {
        titulo: 'Estudar Vue.js',
        finalizada: false
      },
      {
        titulo: 'Estudar Vue Router',
        finalizada: false
      },
      {
        titulo: 'Estudar Vuex',
        finalizada: false
      },
      {
        titulo: 'Estudar TypeScript',
        finalizada: true
      },
      {
        titulo: 'Estudar Node.js',
        finalizada: true
      },
      {
        titulo: 'Estudar Express.js',
        finalizada: false
      }
    ]
  })

  const getTarefasPendentes = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
  }

  const getTarefasFinalizadas = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
  }

  const getTarefasFiltradas = () => {
    const { filtro } = estado

    switch (filtro) {      
      case 'pendentes':
        return getTarefasPendentes()
      case 'finalizadas':
        return getTarefasFinalizadas()
      default:
        return estado.tarefas
    }
  }

  const cadastraTarefa = () => {
    const tarefaNova = {
      titulo: estado.tarefaTemp,
      finalizada: false
    }
    estado.tarefas.push(tarefaNova)    
    estado.tarefaTemp = ''
  }

</script>

<template>
  <div class="container">
    <Header :tarefas-pendentes="getTarefasPendentes().length" />
    <Form :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :cadastra-tarefa="cadastraTarefa" :trocar-filtro="evento => estado.filtro = evento.target.value" />
    <TaskList :tarefas="getTarefasFiltradas()" />
  </div>  
</template>
