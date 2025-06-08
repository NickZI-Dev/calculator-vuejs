<script setup>
import { reactive } from "vue";
import Form from "./components/Form.vue";
import Header from "./components/Header.vue";

const state = reactive({
  aritmetica: "somar",
  primeiroValor: 0,
  segundoValor: 0,
  result: 0,
});

const somarValor = () => {
  const { primeiroValor } = state;
  const { segundoValor } = state;
  return (state.result = parseInt(primeiroValor) + parseInt(segundoValor));
};
const subtrairValor = () => {
  const { primeiroValor } = state;
  const { segundoValor } = state;
  return (state.result = parseInt(primeiroValor) - parseInt(segundoValor));
};

const multiplicarValor = () => {
  const { primeiroValor } = state;
  const { segundoValor } = state;
  return (state.result = parseInt(primeiroValor) * parseInt(segundoValor));
};

const dividirValor = () => {
  const { primeiroValor } = state;
  const { segundoValor } = state;
  if (segundoValor !== 0 && primeiroValor !== 0) {
    const dividir = parseInt(primeiroValor) / parseInt(segundoValor);
    state.result = dividir;
    return state.result;
  } else {
    return "Error: divisão por zero!";
  }
};
const aritmeticaFuncional = () => {
  const { aritmetica } = state;

  switch (aritmetica) {
    case "somar":
      return somarValor();
    case "subtrair":
      return subtrairValor();
    case "multiplicar":
      return multiplicarValor();
    case "dividir":
      return dividirValor();
  }
};
</script>

<template>
  <div class="container">
    <Header></Header>
    <main class="mt-4">
      <Form
        :get-first-value="(event) => (state.primeiroValor = event.target.value)"
        :change-sign="(event) => (state.aritmetica = event.target.value)"
        :get-second-value="(event) => (state.segundoValor = event.target.value)"
        :aritmetica-funcional="aritmeticaFuncional()"
      ></Form>
    </main>
  </div>
</template>

<style scoped></style>
