<template>
    <div v-if="resultado" class="resultado">
        <h3>Resultado para: {{ resultado.nome }}</h3>
        <p>Seu IMC é: <strong>{{ resultado.valorIMC }}</strong></p>
        <p>Classificação: {{ resultado.classificacao }}</p>
    </div>
</template>

<script>
    export default {
        props: ['resultado']
    }
</script>

<style scoped>
.resultado { margin-top: 20px; padding: 15px; border: 2px solid #42b983; border-radius: 8px; background: #f9f9f9; }
</style>