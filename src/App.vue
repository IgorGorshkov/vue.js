<template>
  <div id="app">
    <div class="wrapper">
      <header>
        <h1 class="title">My personal Cost</h1>
      </header>
      <main>
        <add-payment
          v-if="addBtnIsShown"
          @cancelEmit="emitAction"
          @saveEmit="addPayment"
        />
        <button
          class="add-btn"
          @click="addBtnIsShown = !addBtnIsShown"
          v-if="!addBtnIsShown"
        >
          Add new cost +
        </button>
        <payments-display :items="paymentsList" />
        <pagination :selectList="paymentsList" />
      </main>
    </div>
  </div>
</template>

<script>
import AddPayment from "./components/addPayment.vue";
import PaymentsDisplay from "./components/PaymentDisplay.vue";

export default {
  name: "App",
  components: {
    PaymentsDisplay,
    AddPayment,
  },

  data() {
    return {
      paymentsList: [],
      addBtnIsShown: false,
    };
  },
  methods: {
    addPayment(data) {
      this.paymentsList.push(data);
    },
    emitAction() {
      this.addBtnIsShown = false;
    },
    fetchData() {
      return [
        {
          date: "24.04.2022",
          category: "Food",
          value: "123",
        },
        {
          date: "24.04.2022",
          category: "Transport",
          value: "13",
        },
        {
          date: "24.04.2022",
          category: "Housing",
          value: "12",
        },
        {
          date: "24.04.2022",
          category: "Health",
          value: "143",
        },
        {
          date: "24.04.2022",
          category: "Cloth",
          value: "34",
        },
        {
          date: "24.04.2022",
          category: "House",
          value: "11",
        },
      ];
    },
  },
  created() {
    this.paymentsList = this.fetchData();
  },
};
</script>

<style lang="scss" scoped>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.add-btn {
  width: 120px;
  height: 30px;
  background-color: green;
  color: white;
}
</style>