<template>
  <button class="add-coast__btn" @click="addCoast"></button>
</template>

<script>
export default {
  name: "addCoast",
  data() {
    return {};
  },
  methods: {
    addCoast() {
      console.log("addCoast");
    },
  },
};
</script>

<style scoped>
.add-coast__btn {
  width: 100px;
  height: 30px;
  background-color: green;
}
</style>