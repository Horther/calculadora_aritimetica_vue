<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    numero1: 0,
    numero2: 0,
    operacao: 'soma',
    resultado: 0
  })
  const calcula = () =>{
    switch(estado.operacao){
      case 'soma':
        estado.resultado = estado.numero1 + estado.numero2;
        break
      case 'sub':
        estado.resultado = estado.numero1 - estado.numero2;
        break;
      case 'mult':
        estado.resultado = estado.numero1 * estado.numero2;
        break;
      case 'div':
        estado.resultado = estado.numero2 !== 0 ? (estado.numero1 / estado.numero2) : 'Não se divide por 0';
        break;
      case 'pow': 
        estado.resultado = Math.pow(estado.numero1, estado.numero2);
        break;
      case 'raiz':
        estado.resultado = Math.sqrt(estado.numero1);
        break;
    }
  } 


</script>

<template>
  <div class="container p-5 mb-4 mt-4 bg-dark rounded-4 text-center">
    <h1 class="text-light">Calculadora</h1>
    <select class="pb-1 text-center" v-model="estado.operacao">
      <option value="soma" >Soma</option>
      <option value="sub">Subtração</option>
      <option value="mult">Multiplicação</option>
      <option value="div">Divisão</option>
      <option value="pow">Potencia</option>
      <option value="raiz">Raiz Quadrada</option>
    </select>
    <div class="pt-3">
      <input class="me-3" type="number" v-model.number="estado.numero1" @keyup="calcula()">
      <input class="" type="number" v-model.number="estado.numero2" @keyup="calcula()">
    </div>
    <div class="pt-4 pb-3">
      <span class="text-light fs-3">{{estado.resultado}}</span>
    </div>
  </div>
</template>

<style scoped>

</style>
