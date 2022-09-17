<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <div class="display">
      <input placeholder="0" v-model.number="operand1" />
      <input placeholder="0" v-model.number="operand2" />
      <button @click="getResult">=</button>
      {{ result }}
    </div>
    <div v-if="error" class="error">Ошибка! {{ error }}</div>
    <div class="keyboard">
      <button
        v-for="(operator, index) in operators"
        :key="index"
        class="keyboard-btn"
      >
        {{ operator }}
      </button>
      <!-- <button @click="operator = '-'">-</button>
      <button @click="operator = '/'">/</button>
      <button @click="operator = '*'">*</button>
      <button @click="operator = '^'">^</button>
      <button @click="operator = '%'">%</button> -->
    </div>

    <!-- <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: "App",
  // components: {
  //   HelloWorld
  // }
  name: "Calculator",
  data() {
    return {
      operand1: "",
      operand2: "",
      operators: ["+", "-", "*", "/"],
      result: 0,
      error: "",
    };
  },

  methods: {
    getResult() {
      switch (this.operators) {
        case "+":
          this.result = this.operand1 + this.operand2;
          break;
        case "-":
          this.result = this.operand1 - this.operand2;
          break;
        case "/":
          if (operand2 === 0) {
            this.error = "Делить на 0 нельзя!";
          }
          this.result = this.operand1 / this.operand2;
          break;
        case "*":
          this.result = this.operand1 * this.operand2;
          break;
        case "^":
          this.result = Math.pow(+this.operand1, +this.operand2);
          break;
        case "%":
          this.result = this.operand1 % this.operand2;
          break;

        default:
          this.result = "Error";
          break;
      }
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  // width: 1140px;
}
.keyboard-btn {
  margin: 10px;
}
</style>
