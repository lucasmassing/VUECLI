<template>
    <div class="form">
        <input v-model ="nome" placeholder="Digite seu nome" type="text"/>
        <input v-model.number ="peso" placeholder="Peso (kg)" type="number"/>
        <input v-model.number ="altura" placeholder="Altura (ex: 1.75)" type="number"/>
        <button @click="enviarDados">Calcular</button>
    </div>
</template>

<script>
    export default {
    data() {
        return { nome: '', peso: '', altura: '' }
    },
    methods: {
        enviarDados() {
        if (this.nome && this.peso && this.altura) {
            this.$emit('calcular', { nome: this.nome, peso: this.peso, altura: this.altura });
        } else {
            alert("Preencha todos os campos!");
        }
        }
    }
    }
</script>

<style scoped>
.form { display: flex; flex-direction: column; gap: 10px; max-width: 300px; margin: auto; }
input, button { padding: 10px; border-radius: 4px; border: 1px solid #ccc; }
button { background-color: #42b983; color: white; cursor: pointer; font-weight: bold; }
</style>