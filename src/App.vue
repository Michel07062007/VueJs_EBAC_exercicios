<script setup>
import {ref, computed } from 'vue';

const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref('+');

const resultado = computed (() => {
  const n1 = Number(numero1.value)
  const n2 = Number(numero2.value)
  if (Number.isNaN(n1) || Number.isNaN(n2));

    switch (operacao.value) {
      case '+': return n1 + n2;
      case '-': return n1 - n2;
      case '*': return n1 * n2;
      case '/': return n2 !== 0 ? n1 / n2: 'Erro: Divisão por zero';
      default: return 0;
    }
})
</script>

<template>
  <div class="calculadora">
    <h1>Calculadora Aritmética</h1>
    
    <!-- Campos para inserção de números -->
    <input class="opcoes" type="number" v-model="numero1" placeholder="Digite o primeiro número">
    <!-- Campo select para escolher a operação -->
    <select class="opcoes" style="margin: 0px 10px 0px 0px;" v-model="operacao">
      <option value="+">Soma (+)</option>
      <option value="-">Subtração (-)</option>
      <option value="*">Multiplicação (*)</option>
      <option value="/">Divisão (/)</option>
    </select>
    <input class="opcoes" type="number" v-model="numero2" placeholder="Digite o segundo número">
    
    
    <h2>Resultado: {{ resultado }}</h2>
    
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

#app {
  display: grid;
  place-items: center; /* Centraliza horizontal e verticalmente */
  height: 100vh;
}

h1, h2 {
  padding: 50px;
}

input {
  padding-right: 20px;
  margin-right: 10px;
}
</style>
