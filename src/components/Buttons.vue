<template>
  <div class="calculator">
    <div class="display">
      <input type="text" class="calculator-screen" :value="current" disabled />
    </div>
    <div class="buttons">
      <button class="btn clear" @click="clear">C</button>
      <button class="btn backspace" @click="backspace">←</button>
      <button class="btn divide" @click="divide">÷</button>
      <button class="btn multiply" @click="times">×</button>

      <button class="btn number" @click="append('7')">7</button>
      <button class="btn number" @click="append('8')">8</button>
      <button class="btn number" @click="append('9')">9</button>
      <button class="btn subtract" @click="subtract">−</button>

      <button class="btn number" @click="append('4')">4</button>
      <button class="btn number" @click="append('5')">5</button>
      <button class="btn number" @click="append('6')">6</button>
      <button class="btn add" @click="add">+</button>

      <button class="btn number" @click="append('1')">1</button>
      <button class="btn number" @click="append('2')">2</button>
      <button class="btn number" @click="append('3')">3</button>
      <button class="btn number" @click="append('0')">0</button>
      <button class="btn equal" @click="equal">=</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      previous: null,
      current: "",
      operator: null,
      operatorClicked: false,
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (number1, number2) => number1 / number2;
      this.setPrevious();
    },
    times() {
      this.operator = (number1, number2) => number1 * number2;
      this.setPrevious();
    },
    subtract() {
      this.operator = (number1, number2) => number1 - number2;
      this.setPrevious();
    },
    add() {
      this.operator = (number1, number2) => number1 + number2;
      this.setPrevious();
    },
    equal() {
      if (this.operator && this.previous !== null) {
        this.current = `${this.operator(
          parseFloat(this.previous),
          parseFloat(this.current)
        )}`;
        this.previous = null;
      }
    },
    backspace() {
      this.current = this.current.slice(0, -1);
    },
  },
};
</script>

<style scoped>
.calculator {
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  width: 300px;
  padding: 20px;
}

.display {
  margin-bottom: 20px;
}

.calculator-screen {
  width: 100%;
  height: 50px;
  background: #222;
  color: #fff;
  font-size: 1.5rem;
  border: none;
  text-align: right;
  padding: 0 10px;
  border-radius: 5px;
}

.calculator-screen:disabled {
  opacity: 0.8;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.btn {
  background: #f2f2f2;
  border: none;
  border-radius: 5px;
  font-size: 1.2rem;
  padding: 15px;
  cursor: pointer;
  text-align: center;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #ddd;
}

.btn.equal {
  background-color: #007bff;
  color: #fff;
  grid-column: span 2;
}

.btn.equal:hover {
  background-color: #0056b3;
}

.btn.clear {
  background-color: #ff4d4d;
  color: #fff;
}

.btn.clear:hover {
  background-color: #cc0000;
}

.btn.zero {
  grid-column: span 2;
}
</style>
