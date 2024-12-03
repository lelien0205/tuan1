<script setup>
import { computed, ref } from "vue";

const firstName = ref("Nguyen Van");
const lastName = ref("A");
const fullName = computed({
  get() {
    return firstName.value + " " + lastName.value;
  },
  set(newValue) {
    [firstName.value, lastName.value] = newValue.split(",");
  },
});

const changeFullName = () => {
  fullName.value = "Nguyen Van,B";
};
</script>

<template>
  <div>
    <p id="count">Fullname: {{ fullName }}</p>
    <p id="count">First Name: {{ firstName }}</p>
    <p id="count">Last Name: {{ lastName }}</p>

    <button @click="changeFullName">change FullName</button>
  </div>
</template>
