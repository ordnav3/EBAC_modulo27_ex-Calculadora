<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/cabecalho.vue'

const estado = reactive({
  operacoes: 'adicao',
  num1: 0,
  num2: 0,
});

const res = () => {
  switch (estado.operacoes) {
    case 'adicao':
      return Number(estado.num1) + Number(estado.num2)

    case 'subtracao':
      return Number(estado.num1) - Number(estado.num2)

    case 'multiplicacao':
      return Number(estado.num1) * Number(estado.num2)

    case 'divisao':
      return Number(estado.num1) / Number(estado.num2)
  }
}
</script>

<template>
  <div class="container mt-5">
    <Cabecalho />
    <form class="mb-2 text-center p-2" action="">
      <div class="d-flex justify-content-center mb-3">
        <input @keyup="evento => estado.num1 = evento.target.value" type="number">
        <select @change="evento => estado.operacoes = evento.target.value" class="form-control" name="" id="">
          <option value="adicao">+</option>
          <option value="subtracao">-</option>
          <option value="multiplicacao">×</option>
          <option value="divisao">÷</option>
        </select>
        <input @keyup="evento => estado.num2 = evento.target.value" type="number">
      </div>
    </form>
      <p class="bg-light w-100 text-center p-2">Resposta: {{ res() }}</p>
  </div>
</template>

<style scoped>
input, .form-control{
  width: 125px;
  height: 150px;
  text-align: center;
  font-size: 100px;
}

p{
  font-size: 75px;
}

select {
  width: 100px;
  font-size: 75px;
}

option {
  font-size: 25px;
}

input[type=number]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
input[type=number] {
  -moz-appearance: textfield;
  appearance: textfield;
}
</style>