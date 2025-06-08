<script setup>
const props = defineProps([
  "aritmeticaFuncional",
  "getFirstValue",
  "getSecondValue",
  "changeSign",
]);
</script>

<template>
  <form @submit.prevent="" class="input-number">
    <div class="row">
      <div class="col-md-2">
        <input
          @change="props.getFirstValue"
          type="number"
          class="form-control text-center"
          min="0"
          value="0"
        />
      </div>
      <div class="col-md-2">
        <select @change="props.changeSign" class="form-control text-center">
          <option value="somar">+</option>
          <option value="subtrair">-</option>
          <option value="multiplicar">x</option>
          <option value="dividir">÷</option>
        </select>
      </div>
      <div class="col-md-2">
        <input
          @change="props.getSecondValue"
          type="number"
          class="form-control text-center"
          min="0"
          value="0"
        />
      </div>
      <div class="col-md-3">
        <span class="form-control d-flex justify-content-center ms-3">{{
          props.aritmeticaFuncional
        }}</span>
      </div>
    </div>
  </form>
</template>

<style scoped>
.input-number {
  max-width: 640px;
  width: 100%;
  padding: 24px;
  border-radius: 4px;
  background-color: #f1f1f1;
}
.input-number input,
span,
select {
  font-size: 10px;
}
</style>
