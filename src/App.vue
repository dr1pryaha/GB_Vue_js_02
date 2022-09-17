<template>
  <div id="app">
    <div class="display">
      <input @focus="focused" v-model="operand1" />
      {{ operator }}
      <input @focus="focused_2" v-model="operand2" />
      <button @click="getResult">=</button>
      {{ result }}
    </div>
    <div class="keyboard">
      <button @click="operator = '+'">+</button>
      <button @click="operator = '-'">-</button>
      <button @click="operator = '/'">/</button>
      <button @click="operator = '*'">*</button>
      <button @click="operator = '^'">^</button>
      <button @click="operator = '%'">%</button>
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
      operand1: "0",
      operand2: "0",
      operator: "+",
      result: 0,
    };
  },

  methods: {
    getResult() {
      switch (this.operator) {
        case "+":
          this.result = +this.operand1 + +this.operand2;
          break;
        case "-":
          this.result = +this.operand1 - +this.operand2;
          break;
        case "/":
          this.result = +this.operand1 / +this.operand2;
          break;
        case "*":
          this.result = +this.operand1 * +this.operand2;
          break;
        case "^":
          this.result = Math.pow(+this.operand1, +this.operand2);
          break;
        case "%":
          this.result = +this.operand1 % +this.operand2;
          break;

        default:
          this.result = "Error";
          break;
      }
    },
    focused() {
      this.operand1 = "";
    },
    focused_2() {
      this.operand2 = "";
    },
  },
};
</script>

<style lang="scss">
// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }
</style>
