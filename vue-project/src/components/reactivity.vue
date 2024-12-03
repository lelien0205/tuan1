<script setup>
import { ref } from "vue";
const count = ref(1);
const increase = () => {
  count.value++;
};

const submitForm = (e) => {
  e.preventDefault();
  count.value++;
};
</script>

<template>
  <form @submit="submitForm">
    <div>Count: {{ count }}</div>
    <button type="submit">Increase</button>
  </form>
  <!-- <button @click="increase">Increase</button> -->
</template>
