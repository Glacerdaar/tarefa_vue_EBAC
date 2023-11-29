
<template>
  <div class="container p-5">
    <div class="display">
      <form class="form-group" action="" @submit.prevent="calculate">
        <input class="display" type="number" v-model="inputStr1">
        <input class="display" type="number" v-model="inputStr2">
        <!-- Remova o botão de "=" para realizar o cálculo automaticamente -->
      </form>
      <div class="result-display">
        Result: {{ result }}
      </div>
    </div>

    <div class="buttons">
      <div class="row">
        <div class="col-auto">
          <select v-model="selectedOperator">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
          </select>
        </div>
      </div>

      <!-- ... seu código restante ... -->

    </div>
  </div>
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      inputStr1: '',
      inputStr2: '',
      result: '',
      selectedOperator: '+',
    };
  },

  watch: {
    inputStr1: 'calculate', // Chama o método calculate quando inputStr1 é alterado
    inputStr2: 'calculate', // Chama o método calculate quando inputStr2 é alterado
    selectedOperator: 'calculate', // Chama o método calculate quando selectedOperator é alterado
  },

  methods: {
    updateDisplay(val) {
      if (!this.result) {
        this.inputStr1 = this.inputStr1 + val;
      } else {
        this.inputStr2 = this.inputStr2 + val;
      }
    },

    calculate() {
      if (this.inputStr1 && this.inputStr2) {
        const expression = `${this.inputStr1} ${this.selectedOperator} ${this.inputStr2}`;
        this.result = eval(expression);
        console.log(this.result);
      }
    },

    clearDisplay() {
      this.inputStr1 = '';
      this.inputStr2 = '';
      this.result = '';
    },
  },
};
</script>

<style scoped>
</style>
