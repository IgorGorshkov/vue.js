<template>
  <div class="add-wrapper">
    <div class="add-info">
      <label for="">Date</label>
      <input class="add-info__input" placeholder="Date" v-model.trim="date" />
    </div>
    <div class="add-info">
      <label for="">Category</label>
      <input
        class="add-info__input"
        placeholder="insert category"
        v-model.trim="category"
      />
    </div>
    <div class="add-info">
      <label for="">Value</label>
      <input placeholder="insert price" v-model="value" />
    </div>
    <div class="add-btns">
      <button class="add-btn__cancel" @click="onCancel">Cancel</button>
      <button class="add-btn__save" @click="onSave">Save</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "addPayment",
  data() {
    return {
      date: "",
      category: "",
      value: 0,
    };
  },
  methods: {
    onSave() {
      const { value } = this;
      const data = {
        date: this.date || this.getCurrentDate,
        category: this.category || "Unsorted",
        value,
      };
      this.$emit("saveEmit", data);
    },
    onCancel() {
      this.$emit("cancelEmit");
    },
  },
  computed: {
    getCurrentDate() {
      const date = new Date();
      const d = date.getDate();
      const m = date.getMonth();
      const y = date.getFullYear();
      return `${d}.${m}.${y}`;
    },
  },
};
</script>

<style scoped>
.add-wrapper {
  width: 80%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
}
.add-info {
  width: 70%;
  margin: 5px auto;
  display: flex;
  justify-content: space-evenly;
}
.add-info__input::placeholder {
  color: #c7c2c1;
}
.add-btns {
  width: 70%;
  margin: 20px auto 10px;
  display: flex;
  justify-content: space-evenly;
}
.add-btn__save {
  width: 100px;
  height: 30px;
  background-color: green;
  color: white;
}
.add-btn__cancel {
  background-color: red;
  color: white;
  width: 100px;
  height: 30px;
  border-radius: 3px;
}
</style>