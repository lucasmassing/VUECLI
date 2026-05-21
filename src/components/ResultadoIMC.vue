<template>
  <div v-if="resultado" class="resultado-container">
    <div class="feedback-usuario">
      <h3>Olá, {{ resultado.nome }}!</h3>
      <p>Seu IMC é de: <span class="destaque-imc">{{ resultado.valorIMC }}</span></p>
      <p>Sua classificação atual é: <strong>{{ resultado.classificacao }}</strong></p>
    </div>

    <hr />

    <h4>Tabela de Referência:</h4>
    <ul class="tabela-imc">
      <li 
        v-for="(regra, index) in referencias" 
        :key="index"
        :class="{ 'linha-ativa': resultado.classificacao === regra.label }"
      >
        <span>{{ regra.descricao }}</span>
        <strong>{{ regra.label }}</strong>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['resultado'],
  data() {
    return {
      // Array de objetos que será percorrido pelo v-for
      referencias: [
        { descricao: 'IMC menor que 18', label: 'Magro' },
        { descricao: 'IMC entre 18 e 24.99', label: 'Normal' },
        { descricao: 'IMC igual ou maior que 25', label: 'Sobrepeso' }
      ]
    }
  }
}
</script>

<style scoped>
.resultado-container {
  margin-top: 25px;
  text-align: left;
}

.feedback-usuario {
  background-color: #e8f5e9;
  padding: 15px;
  border-radius: 8px;
  border-left: 5px solid #42b983;
  margin-bottom: 20px;
}

.destaque-imc {
  font-size: 1.4rem;
  font-weight: bold;
  color: #2c3e50;
}

hr {
  border: 0;
  border-top: 1px solid #eee;
  margin: 20px 0;
}

h4 {
  margin-bottom: 10px;
  color: #666;
}

.tabela-imc {
  list-style: none;
}

.tabela-imc li {
  display: flex;
  justify-content: space-between;
  padding: 8px 12px;
  border-bottom: 1px solid #f0f0f0;
  color: #555;
  border-radius: 4px;
}

/* Classe dinâmica: se a classificação da pessoa bater com a linha, destaca ela */
.linha-ativa {
  background-color: #42b983;
  color: white !important;
}
.linha-ativa strong {
  color: white;
}
</style>