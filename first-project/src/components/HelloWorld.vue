<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model.number.lazy="operand1" />
    <input v-model.number.lazy="operand2" />
    = {{ result }}
    <br />

    <button @click="sum">+</button>
    <button @click="divide">-</button>
    <button @click="sub">/</button>
    <button @click="multiply">*</button>
    <button @click="pow">Степень числа</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: {
      type: String,
    },
    text: {
      type: String,
    },
  },
  data() {
    return {
      result: 0,
      operand1: 0,
      operand2: 0,
    };
  },
  methods: {
    sum() {
      this.result = this.operand1 + this.operand2;
    },
    divide() {
      this.result = this.operand1 - this.operand2;
    },
    sub() {
      if (this.operand2 === 0) {
        alert(`На ${this.operand2} делить нельзя`);
      } else {
        this.result = this.operand1 / this.operand2;
      }
    },
    multiply() {
      this.result = this.operand1 * this.operand2;
    },
    pow() {
      this.result = Math.pow(this.operand1, this.operand2);
    },
  },
};
</script>

<style scoped lang="scss">
</style>
