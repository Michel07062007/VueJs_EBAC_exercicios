<script setup>
data: {
  numero1: 0
  numero2: 0
  operacao: '+'
  resultado: 0
}
watch: {
  // Usar watch para monitorar as mudanças e calcular automaticamente
  numero1(); {
    this.calcular()
  }
  numero2(); {
    this.calcular()
  }
  operacao(); {
    this.calcular()
  }
}
watch: {
  calcular(); {
    const n1 = parseFloat(this.numero1);
    const n2 = parseFloat(this.numero2);
    if (isNaN(n1) || isNaN(n2)) {
      this.resultado = 0;
      return;
    }
    switch (this.operacao) {
      case '+':
        this.resultado = n1 + n2;
        break;
      case '-':
        this.resultado = n1 - n2;
        break;
      case '*':
        this.resultado = n1 * n2;
        break;
      case '/':
        if (n2 !== 0) {
          this.resultado = n1 / n2;
        } else {
          this.resultado = 'Erro: Divisão por zero';
        }
        break;
      default:
        this.resultado = 0;
    }
  }
}
</script>

<template>
  <div class="calculadora">
    <h1>Calculadora Aritmética</h1>
    
    <!-- Campos para inserção de números -->
    <input type="number" v-model="numero1" placeholder="Digite o primeiro número">
    <input type="number" v-model="numero2" placeholder="Digite o segundo número">
    
    <!-- Campo select para escolher a operação -->
    <select v-model="operacao">
      <option value="+">Soma (+)</option>
      <option value="-">Subtração (-)</option>
      <option value="*">Multiplicação (*)</option>
      <option value="/">Divisão (/)</option>
    </select>
    
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
</style>
