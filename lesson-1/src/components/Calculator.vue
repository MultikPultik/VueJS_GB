<template>
  <div>
    <h1>Калькулятор</h1>

    <div class="display">
      <input type="number" v-model.number="operand1" />
      <input type="number" v-model.number="operand2" />
      = {{ result }}
    </div>

    <div class="keyboard">
      <div class="keyboard_operand">
        <button
          v-for="operation in operations"
          @click="calculate(operation)"
          v-bind:key="operation"
          v-bind:title="operation"
        >
          {{ operation }}
        </button>
      </div>

      <div class="keyboard_numbers">
        <button v-for="(number,index) in 10" v-bind:key="number">
          {{ index }}
        </button>
      </div>
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
      operations: ["+", "-", "*", "/", "^", "INTDIV"],
      
      result: 0,
    };
  },
  methods: {
    calculate(op) {
      switch (op) {
        case "+":
          this.add();
          break;
        case "-":
          this.sub();
          break;
        case "*":
          this.mul();
          break;
        case "/":
          this.divison();
          break;
        case "^":
          this.pow();
          break;
        case "INTDIV":
          this.intdiv();
          break;
      }
    },

    add() {
      this.result = this.operand1 + this.operand2;
    },

    sub() {
      this.result = this.operand1 - this.operand2;
    },

    mul() {
      this.result = this.operand1 + this.operand2;
    },

    pow() {
      this.result = Math.pow(this.operand1, this.operand2);
    },

    divison() {
      if (this.operand2 === 0) {
        this.result = "Ошибка! (Деление на '0')";
      } else {
        this.result = this.operand1 / this.operand2;
      }
    },

    intdiv() {
      if (this.operand2 === 0) {
        this.result = "Ошибка! (Деление на '0')";
      } else {
        this.result = parseInt(this.operand1 / this.operand2);
      }
    },
  },
};
</script>

<style scoped>
.keyboard_numbers {
  width: 150px;
  display: flex;
  flex-wrap: wrap;
}
.keyboard_numbers button {
  width: 50px;
  height: 50px;
  border-radius: 6px;
}
</style>