<script setup>
    const props = defineProps(['respostaDaOperacao']);
</script>

<template>
    <h1 class="igual">=</h1>
    <span v-if="props.respostaDaOperacao >= 0">{{props.respostaDaOperacao}}</span><span v-else>Preencha os campos</span>
</template>

<style scoped>
    h1 {
    font-size: 50px;
    background-color: #f2faef;
    }

    span{
    font-size: 30px;
    background-color: hsl(188, 70%, 89%);
    border: 1px solid black;
    border-radius: 10px;
    }
</style>