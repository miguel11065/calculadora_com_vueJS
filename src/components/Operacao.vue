<script setup>
    const props = defineProps(['numero1', 'numero2', 'selecionaOperacao'])
</script>

<template>
    <input type="number" required @keyup="props.numero1">
    <select @change="props.selecionaOperacao">
        <option value="soma">+</option>
        <option value="sub">-</option>
        <option value="div">÷</option>
        <option value="mult">x</option>
    </select>
    <input type="number" required @keyup="props.numero2">
</template>

<style scoped>
    input{
    padding: 10px;
    width: 100%;
    font-size: 30px;
    border-radius: 10px;
    border: 1px solid black;
    background-color: hsl(188, 70%, 89%);
    }

    select{
    padding: 10px;
    width: 100%;
    font-size: 30px;
    border-radius: 10px;
    border: 1px solid black;
    background-color: hsl(188, 70%, 89%);
    }
</style>