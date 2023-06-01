<script setup>
import { reactive } from 'vue';

const calcular = reactive({
  campoA: '',
  campoB: '',
  calcularTotal: 'soma',
  
})


const getSomarNumeros = () => {
  const { campoA, campoB } = calcular;
  return Number(campoA) + Number(campoB);
}

const getSubtrairNumeros = () => {
  const { campoA, campoB } = calcular;
  return Number(campoA) - Number(campoB);
}

const getMultiplicarNumeros = () => {
  const { campoA, campoB } = calcular;
  return Number(campoA) * Number(campoB);
}

const getDividirNumeros = () => {
  const { campoA, campoB } = calcular;
  return Number(campoA) / Number(campoB)
}

const getFiltrarCalculos = () => {
  const {calcularTotal} = calcular;


switch (calcularTotal) {
  case 'somar':
    return getSomarNumeros();
  case 'subtrair':
    return getSubtrairNumeros();
  case 'multiplicar':
    return getMultiplicarNumeros();
  case 'dividir':
    return getDividirNumeros().toFixed(2)
  }
}
</script>

<template>
  <div class="container">
    <header class="p-3 mb-2 mt-4 bg-light rounded-3 ">
      <h1>Calculadora Aritmética</h1>
    </header>
    <form>
      <input required :value="calcular.campoA" @change="evento => calcular.campoA = evento.target.value" type="number" placeholder="Insira um número">
      <select @change="evento => calcular.calcularTotal  = evento.target.value" class="m-2">
        <option value="somar">Somar</option>
        <option value="subtrair">Subtrair</option>
        <option value="multiplicar">Multiplicar</option>
        <option value="dividir">Dividir</option>
      </select> <br />
      <input required :value="calcular.campoB" @change="evento => calcular.campoB = evento.target.value" class="mt-4 mb-4" type="number" placeholder="Insira um número">
      <input placeholder="Total" :value="getFiltrarCalculos()" class="t-campo">
    </form>
  </div>
</template>

<style scoped>
header {
  text-align: center;
}

.t-campo {
  max-width: 100px;
  margin-left: 6px;
}
</style>
