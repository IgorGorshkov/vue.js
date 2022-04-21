<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input :title="operand1" id="one" v-model.number="operand1" />
    <input :title="operand2" id="two" v-model.number="operand2" />
    = {{ result }}
    <br />
    <div class="error">
      {{ error }}
    </div>
    <div class="keyboard">
      <button
        :title="operand"
        v-for="operand in operands"
        @click="calculate(operand)"
        :key="operand"
      >
        {{ operand }}
      </button>
    </div>
    <hr />
    <br />
    <div class="checkbox">
      <input type="checkbox" id="checkbox" v-model="checked" />
      <label for="checkbox"> Отобразить экранную клавиатуру</label>
      <div class="items" v-if="checked">
        <button v-for="btn in numbers" :key="btn" @click="pressBtn(btn)">
          {{ btn }}
        </button>
        <button @click="remove()">&larr;</button>
        <br />
        <input type="radio" id="operand1" :value="operand1" v-model="picked" />
        <label for="operand1">Операнд 1</label>
        <input type="radio" id="operand2" :value="operand2" v-model="picked2" />
        <label for="operand2">Операнд 2</label>
        <br />
        {{ error2 }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: {
      type: String,
    },
  },
  data() {
    return {
      result: 0,
      operand1: 0,
      operand2: 0,
      error: "",
      operands: ["+", "-", "/", "*"],
      numbers: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      checked: false,
      error2: "",
      picked: "",
      picked2: "",
    };
  },
  methods: {
    calculate(operation = "+") {
      this.error = "";
      switch (operation) {
        case "+":
          this.sum();
          break;
        case "-":
          this.sub();
          break;
        case "/":
          this.divide();
          break;
        case "*":
          this.multiply();
          break;
      }
    },
    sum() {
      this.result = +this.operand1 + +this.operand2;
    },
    sub() {
      this.result = this.operand1 - this.operand2;
    },
    divide() {
      const { operand1, operand2 } = this;
      if (operand2 === 0) {
        this.error = "Делить на 0 нельзя";
        return;
      } else {
        this.result = operand1 / operand2;
      }
    },
    multiply() {
      this.result = this.operand1 * this.operand2;
    },
    pressBtn(btn) {
      if (this.picked === this.operand1) {
        this.operand1 = +`${this.operand1}${btn}`;
      } else if (this.picked2 === this.operand2) {
        this.operand2 = +`${this.operand2}${btn}`;
      } else {
        this.error2 = "Выберите Операнд";
      }
    },
    remove() {
      if (this.picked === this.operand1) {
        this.operand1 = "";
      } else if (this.picked2 === this.operand2) {
        this.operand2 = "";
      } else {
        this.error2 = "Выберите Операнд";
      }
    },
    // clear() {
    //   if (!isNaN(this.operand1[this.operand1.length - 1])) {
    //     this.operand1 = this.operand1.substring(0, this.operand1.length - 1);
    //   } else {
    //     !isNaN(this.operand2[this.operand2.length - 1]);
    //     this.operand2 = this.operand2.substring(0, this.operand2.length - 1);
    //   }
    // },
  },
};
</script>

<style scoped lang="scss">
.items {
  padding: 20px 0;
}
</style>
