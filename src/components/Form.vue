<script setup>
const props = defineProps(['getOperacao', 'estado'])
const input1 = defineModel('input1')
const input2 = defineModel('input2')
const filtro = defineModel('filtro')
</script>

<template>
    <form @submit.prevent="props.getOperacao">
        <div class="row justify-content-center">
            <input v-model.number="input1" type="number" placeholder="Digite o primeiro número" class="col-md-2 me-2" required />
            <input v-model.number="input2" type="number" placeholder="Digite o segundo número" class="col-md-2 me-2" required />
            <select v-model="filtro" class="col-md-2">
                <option v-for="operacao in props.estado.operacoes" :key="operacao">{{ operacao }}</option>
            </select>
        </div>
    </form>
</template>