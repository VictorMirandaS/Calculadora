<script setup>
import { reactive } from 'vue';

const estado = reactive({
    primeiroNumero: '',
    segundoNumero: '',
    operacoes: {
        soma: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Divisão por zero'),
    },
    resultado: 0,
});

const calculaResultado = () => {
    const { primeiroNumero, segundoNumero, operacaoMatematica } = estado;
    const num1 = parseFloat(primeiroNumero);
    const num2 = parseFloat(segundoNumero);
    estado.resultado = !isNaN(num1) && !isNaN(num2) ? estado.operacoes[operacaoMatematica](num1, num2) : 'Entrada inválida';
};
</script>

<template>
    <div class="container">
        <h1 class="title">Calculadora Aritmética</h1>
        <div class="calculator">
            <input class="input-field" type="number" v-model="estado.primeiroNumero" @input="calculaResultado"
                placeholder="Primeiro número" />
            <input type="number" class="input-field" v-model="estado.segundoNumero" @input="calculaResultado"
                placeholder="Segundo número" />
            <select class="operation-select" v-model="estado.operacaoMatematica" @change="calculaResultado">
                <option value="soma">Soma</option>
                <option value="subtracao">Subtração</option>
                <option value="multiplicacao">Multiplicação</option>
                <option value="divisao">Divisão</option>
            </select>
            <p class="result">
                Resultado: <span>{{ estado.resultado }}</span>
            </p>
        </div>
    </div>
</template>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}

.title {
    margin: 20px 0;
    font-size: 1.8em;
    color: #333;
}

.calculator {
    width: 100%;
    max-width: 400px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #f9f9f9;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

.input-field,
.operation-select {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    font-size: 1em;
    border: 1px solid #ddd;
    border-radius: 5px;
    text-align: center;
}

.result {
    margin-top: 20px;
    font-size: 1.2em;
    font-weight: bold;
    color: #333;
}

.result span {
    color: #007bff;
}

/* Responsividade */
@media (max-width: 500px) {
    .title {
        font-size: 1.5em;
    }

    .calculator {
        padding: 15px;
    }

    .input-field,
    .operation-select {
        font-size: 0.9em;
    }

    .result {
        font-size: 1em;
    }
}
</style>
