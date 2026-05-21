<template>
  <div id="app">
    <div class="container">
      <HeaderApp />
      <FormularioIMC @calcular="efetuarCalculo" />
      <ResultadoIMC :resultado="dadosFinais" />
    </div>
  </div>
</template>

<script>
import HeaderApp from './components/HeaderApp.vue'
import FormularioIMC from './components/FormularioIMC.vue'
import ResultadoIMC from './components/ResultadoIMC.vue'

export default {
  name: 'App',
  components: { HeaderApp, FormularioIMC, ResultadoIMC },
  data() {
    return {
      dadosFinais: null
    }
  },
  methods: {
    efetuarCalculo(dados) {
      const imc = (dados.peso / (dados.altura * dados.altura)).toFixed(2);
      let classificacao = '';

      if (imc < 18) classificacao = 'Magro';
      else if (imc < 25) classificacao = 'Normal';
      else classificacao = 'Sobrepeso';

      this.dadosFinais = {
        nome: dados.nome,
        valorIMC: imc,
        classificacao: classificacao
      };
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f4f7f6;
  color: #333;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

#app {
  width: 100%;
  max-width: 500px;
  padding: 20px;
}

.container {
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}
</style>