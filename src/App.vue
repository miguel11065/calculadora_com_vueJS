<script setup>
  import { reactive } from 'vue';


  const estado = reactive ({
    operacao: 'soma',
    numero1: 0,
    numero2: 0,
  });


  const soma = () =>{
    return parseInt(estado.numero1)+ parseInt(estado.numero2)
  }

  const subtracao = () =>{
    return estado.numero1 - estado.numero2
  }

  const divisao = () =>{
    return estado.numero1 / estado.numero2
  }

  const multiplicacao = () =>{
    return estado.numero1 * estado.numero2
  }

  const operacoes = () => {
      const {operacao} = estado;
      switch (operacao){
        case 'soma':
          return soma();
        case 'sub':
          return subtracao();
        case 'div':
          return divisao();
        case 'mult':
          return multiplicacao();  
      }
  }

  const valorPadrao = () => {
    if(estado.numero1 === ''){
      estado.numero1 = 0
    }
  }

</script>

<template>
  <div class="container">
    <header class="p-3 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora</h1>
    </header>
    <input type="number" required @keyup="evento => estado.numero1 = evento.target.value">
    <select @change="evento => estado.operacao = evento.target.value">
      <option value="soma">+</option>
      <option value="sub">-</option>
      <option value="div">÷</option>
      <option value="mult">x</option>
    </select>
    <input type="number" required @keyup="evento => estado.numero2 = evento.target.value">
    <h1 class="igual">=</h1>
    <span v-if="operacoes() >= 0">{{operacoes()}}</span><span v-else>Preencha os campos</span>
  </div>
</template>

<style scoped>
  .container{
    display: flex;
    flex-direction: column;
    padding: 35px;
    max-width: 600px;
    gap: 10px;
    align-items: center;
    margin: 5vh auto;
    border-radius: 50px;
    background-image: url(https://img.freepik.com/vetores-premium/numeros-e-operacoes-matematicas-sem-costura-padrao-aritmetica-ilustracao-vetorial-de-fundo_449806-433.jpg?w=2000);
    background-size: cover;
    padding-top: 0;
    border: 1px solid black;
  }

  h1 {
    font-size: 50px;
    background-color: #f2faef;
  }

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

  span{
    font-size: 30px;
    background-color: hsl(188, 70%, 89%);
    border: 1px solid black;
    border-radius: 10px;
  }
</style>