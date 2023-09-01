<script setup>
import { reactive } from 'vue';

const estadoApp = reactive({
  primeiroNumero: 0,
  segundoNumero: 0,
  operacao: "+",
  resultado:0
})

function realizarOperacao(){
  estadoApp.resultado = eval(`${estadoApp.primeiroNumero} ${estadoApp.operacao[0]} ${estadoApp.segundoNumero}`)
}
function atualizarN1(evt){
  estadoApp.primeiroNumero = evt.target.value
  realizarOperacao()
}
function atualizarN2(evt){
  estadoApp.segundoNumero = evt.target.value
  realizarOperacao()
}
function atualizarOp(evt){
  estadoApp.operacao = evt.target.value
  realizarOperacao()
}

</script>

<template>
  <main>
    <h1>Calculadora simples</h1>
    <form>
      <div>
        <input type="number" placeholder="digite um número" :value="estadoApp.primeiroNumero" @keyup="atualizarN1">
        <span> {{ estadoApp.operacao }}</span>
        <input type="number" placeholder="digite um número" :value="estadoApp.segundoNumero" @keyup="atualizarN2">
        <span>{{ estadoApp.resultado }}</span>
        <hr>
        <span>Escolha uma operação</span>
          <select @change="atualizarOp">
            <option value='+' selected>somar</option>
            <option value='-'>subtrair</option>
            <option value='/'>dividir</option>
            <option value='*'>multiplicar</option>
          </select>
      </div>
    </form>
  </main>
</template>

<style scoped>
main {
  max-width: 300px;
  height: 400px;
  max-height: 500px;
  margin: 10vh auto;
  padding: 1em;
  border: 1px solid black;
  border-radius: 25px;
  background-color: lightgray;
}
hr {
  width: 100%;
}
form>div {
  display: flex;
  flex-direction: column;
  gap: 0.5em;
}

form>div>input {
  text-align: right;
  height: 1.5em;
  font-size: 1.5em;
  padding: 0 .2em;
}
form>div>span,
form>div>select {
  font-size: 1.5em;
  text-align: center;
}

</style>
