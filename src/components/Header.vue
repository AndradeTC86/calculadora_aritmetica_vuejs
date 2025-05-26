<script setup>
    const props = defineProps(['resultado'])
</script>

<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Calculadora Aritmética VueJS</h1>
        <p>
            O resultado da operação é: <strong>{{ props.resultado }}</strong>
        </p>
    </header>
</template>