<script setup>
  import { reactive } from 'vue';
  import Tela from './components/Tela.vue';
  import Formulario from './components/Formulario.vue';
  import Historico from './components/Historico.vue';

const estado = reactive({
  valorUm: 0,
  valorDois: 0,
  operacao: '+',
  resultado: 0,
  historico: [],
})

const calcular = () => {
  const { valorUm, valorDois, operacao } = estado;

  switch (operacao) {
    case '+':
      estado.resultado = valorUm + valorDois;
      break;
    case '-':
      estado.resultado = valorUm - valorDois;
      break;
    case '/':
      estado.resultado = valorUm / valorDois;
      break;
    case '*':
      estado.resultado = valorUm * valorDois;
      break
    default:
      return estado.resultado = 0;
  }

  return estado.resultado
}

const limpar = () => {
  estado.valorUm = 0;
  estado.valorDois = 0;
}

const enviarHistorico = (e) => {
  const novoHistorico = {
    valorHistoricoUm: estado.valorUm,
    valorHistoricoDois: estado.valorDois,
    operacaoHistorico: estado.operacao,
    resultadoHistorico: calcular(),
    id: parseInt(Math.random() * 10000),
  }

  if (!isNaN(novoHistorico.resultadoHistorico)) {
    estado.historico.push(novoHistorico);
  } else {
    alert('Não há dados')
  }
}

const deleteHistorico = (e) => {
  const { historico } = estado;

  const button = e.target;
  const idButton = Number(button.id);

  const indice = historico.findIndex(obj => obj.id === idButton);


  if (indice !== -1) {
    historico.splice(indice, 1)
  }
}

</script>

<template>
  <div class="container d-flex flex-column align-items-center">
    <Tela :valor-um="estado.valorUm" :valor-dois="estado.valorDois" :operacao="estado.operacao" :calcular="calcular()"/>
    <Formulario :enviar-historico="enviarHistorico" :limpar="limpar" :get-valor-um="evento => estado.valorUm = evento.target.value" :get-valor-dois="evento => estado.valorDois = evento.target.value" :get-operacao="evento => estado.operacao = evento.target.value"/>
    <Historico :historico="estado.historico" :delete-historico="deleteHistorico" />
  </div>
</template>

<style scoped>

</style>
