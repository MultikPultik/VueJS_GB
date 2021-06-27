<template>
  <div>
    <h1>Калькулятор</h1>

    <div class="display">
      <input type="number" v-model.number="operand1" />
      <input type="number" v-model.number="operand2" />
      = {{ result }}
    </div>

    <div class="keyboard">
      <button @click="result = operand1 + operand2">+</button>
      <button @click="result = operand1 - operand2">-</button>
      <button @click="result = operand1 * operand2">*</button>
      <button @click="divison(operand1, operand2)">/</button>
      <button @click="pow(operand1, operand2)">^</button>
      <button @click="intdiv(operand1, operand2)">INTDIV</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      operand1: 0,
      operand2: 0,
      result: 0,
    };
  },
  methods: {
    counter() {
      this.val++;
    },

    pow(val1, val2){
      this.result = Math.pow(val1, val2);
    },
    
    divison(val1, val2) {
      if (val2 === 0) {
        this.result = "Ошибка! (Деление на '0')";
      } else {
        this.result = val1 / val2;
      }
    },

    intdiv(val1, val2) {
      if (val2 === 0) {
        this.result = "Ошибка! (Деление на '0')";
      } else {
        this.result = parseInt(val1 / val2);
      }
    },
  },
};
</script>

<style></style>
