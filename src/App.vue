<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Operacao from './components/Operacao.vue';
  import Resposta from './components/Resposta.vue';


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
    <Cabecalho />
    <Operacao :selecionaOperacao="evento=> estado.operacao = evento.target.value" :numero1="evento => estado.numero1 = evento.target.value" :numero2="evento => estado.numero2 = evento.target.value"></Operacao>
    <Resposta :numero1="estado.numero1" :numero2="estado.numero2" :resposta-da-operacao="operacoes()"/>
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
</style>