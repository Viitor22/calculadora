<script setup>
import { reactive } from 'vue';

    const estado = reactive({
        num1: 0.0,
        num2: 0.0,
        filtro: 'soma',
    })

    const getResultado = (estado) => {
    const {filtro} = estado;

    switch (filtro){
        case 'soma':
            const soma = parseInt(estado.num1) + parseInt(estado.num2);
            return soma;

        case 'sub':
            const sub = estado.num1 - estado.num2;
            return sub;

        case 'mult':
            const mult = estado.num1 * estado.num2;
            return mult

        case 'div':
            const div = estado.num1 / estado.num2;
            return div;
    }
    }
</script>

<template>
    <div class ="container">
        <header>
            <h1>Calculadora</h1>
        </header>
        <form id="form-atividade">
            <input @change="evento => estado.num1 = evento.target.value" type="number" required>
            <input @change="evento => estado.num2 = evento.target.value" type="number" required>
            <select @change="evento => estado.filtro = evento.target.value">
                <option value="soma">Soma</option>
                <option value="sub">Subtração</option>
                <option value="mult">Multiplicação</option>
                <option value="div">Divisão</option>
            </select>
        </form>
        <h2>Resultado:</h2>
        <p>{{ getResultado(estado) }}</p>
    </div> 
</template>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
}

body {
    background-color: #f7f7f7;
    padding-top: 100px;
}

header {
    display: flex;
    align-items: center;
    margin-bottom: 40px;
    margin-top: 20vh;
}

header h1{
    font-size: 40px;
    font-weight: bold;
}

.container{
    max-width: 960px;
    width: 100%;
    margin: 0 auto;
}

form{
    display: flex;
    max-width: 640px;
    width: 100%;
    justify-content: space-between;
    margin-bottom: 56px;
}

form input{
    font-size: 24px;
    background-color: #fff;
    border: none;
    border: 2px solid black;
    padding: 8px;
    margin-right: 20px;
}

form select{
    font-size: 24px;
    background-color: #fff;
    border: none;
    border: 2px solid black;
    padding: 8px;
}

h2 {
    font-size: 30px;
    border-bottom: 2px solid black;
    max-width: 150px;
}

p {
    font-size: 30px;
    margin-top: 15px;
}
</style>
