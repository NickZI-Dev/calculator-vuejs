<script setup>
import { reactive } from "vue";

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
  return (state.result = parseInt(primeiroValor) / parseInt(segundoValor));
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
    <header class="mt-4">
      <h1>Calculator-Vue.js</h1>
    </header>
    <main class="mt-4">
      <form @submit.prevent="" class="input-number">
        <div class="row">
          <div class="col-md-2">
            <input
              @change="(event) => (state.primeiroValor = event.target.value)"
              type="number"
              class="form-control text-center"
              min="0"
              value="0"
            />
          </div>
          <div class="col-md-2">
            <select
              @change="(event) => (state.aritmetica = event.target.value)"
              class="form-control text-center"
            >
              <option value="somar">+</option>
              <option value="subtrair">-</option>
              <option value="multiplicar">x</option>
              <option value="dividir">÷</option>
            </select>
          </div>
          <div class="col-md-2">
            <input
              @change="(event) => (state.segundoValor = event.target.value)"
              type="number"
              class="form-control text-center"
              min="0"
              value="0"
            />
          </div>
          <div class="col-md-2">
            <button
              type="submit"
              class="btn btn-primary fw-bold ms-3"
              @click="aritmeticaFuncional"
            >
              =
            </button>
          </div>
          <div class="col-md-3">
            <span
              v-if="state.aritmetica === 'dividir'"
              class="form-control d-flex justify-content-center final-result ms-3"
              >{{ state.result.toFixed(2) }}</span
            >
            <span
              v-else
              class="form-control d-flex justify-content-center final-result ms-3"
            >
              {{ state.result }}
            </span>
          </div>
        </div>
      </form>
    </main>
  </div>
</template>

<style scoped>
.input-number {
  max-width: 640px;
  width: 100%;
  padding: 24px;
  border-radius: 4px;
  background-color: #f1f1f1;
}

.final-result {
  flex-wrap: wrap;
}
</style>
