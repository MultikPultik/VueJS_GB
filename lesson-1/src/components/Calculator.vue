<template>
  <div>
    <h1>Калькулятор</h1>

    <div class="display">
      <input type="number" v-model.number="operand1" @focus="picked = 'Один'" />
      <input type="number" v-model.number="operand2" @focus="picked = 'Два'" />
      = {{ result }}
    </div>

    <br />
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">Отобразить экранную клавиатуру</label>
    <br />
    <br />

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

      <div class="keyboard_numbers" v-show="checked">
        <button
          v-for="(number, index) in 10"
          v-bind:key="number"
          @click="digBtnPressed(index)"
        >
          {{ index }}
        </button>
        <button @click="backSpace()"><i class="fas fa-backspace"></i></button>
      </div>
      <br />
      <div class="choose_operand" v-show="checked">
        <div class="wrap"></div>
        <input type="radio" id="op1" value="Один" v-model="picked" />
        <label for="op1">Операнд 1</label>
        <input type="radio" id="op2" value="Два" v-model="picked" />
        <label for="op2">Операнд 2</label>
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
      operations: ["+", "-", "*", "/", "^", "IDIV"],
      checked: true,
      picked: "Один",
      result: 0,
    };
  },

  methods: {
    digBtnPressed(op) {
      if (this.picked === "Один") {
        if (this.operand1 === 0) {
          this.operand1 = "";
        }
        this.operand1 = "" + this.operand1 + op;
      } else {
        if (this.operand2 === 0) {
          this.operand2 = "";
        }
        this.operand2 = "" + this.operand2 + op;
      }
    },
    backSpace() {
      if (this.picked === "Один") {
        if (this.operand1 === 0) {
          this.operand1 = "";
        }
        this.operand1 = ("" + this.operand1).slice(0, -1);
      } else {
        if (this.operand2 === 0) {
          this.operand2 = "";
        }
        this.operand2 = ("" + this.operand2).slice(0, -1);
      }
    },
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
        case "IDIV":
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
.keyboard {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.keyboard button {
  font-size: 20px;
  padding: 0;
  margin: 1px;
  width: 50px;
  height: 50px;
  border-radius: 6px;
}

.keyboard_numbers {
  width: 159px;
  display: flex;
  flex-wrap: wrap;
}

.keyboard_operand {
  margin-bottom: 10px;
}

.choose_operand label{
  margin-right: 30px;
}
</style>
