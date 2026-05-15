
<template>
  <div id="app">
    <HeaderApp />
    <FormularioIMC @calcular="efetuarCalculo" />
    <ResultadoIMC :resultado="dadosFinais" />
  </div>
</template>

<script>
  import FormularioIMC from './components/FormularioIMC.vue';
  import HeaderApp from './components/HeaderApp.vue';
  import ResultadoIMC from './components/ResultadoIMC.vue';

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

        if (imc < 18.5) classificacao = 'Abaixo do peso';
        else if (imc < 25) classificacao = 'Peso normal';
        else if (imc < 30) classificacao = 'Sobrepeso';
        else classificacao = 'Obesidade';

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
#app { font-family: Avenir, Helvetica, Arial, sans-serif; text-align: center; color: #2c3e50; margin-top: 60px; }
</style>