<script setup>
import { ref } from "vue";
const shoppingItems = ref([
  {
    name: "apple",
    price: 7,
  },
  {
    name: "orange",
    price: 12,
  },
]);

const user = ref([
  {
    name: "John",
    age: 30,
    isActive: true,
  },
  {
    name: "Bob",
    age: 20,
    isActive: false,
  },
  {
    name: "Carol",
    age: 25,
    isActive: true,
  },
]);
</script>

<template>
  <div>
    <ul>
      <li v-for="item in shoppingItems" :key="item.id">
        {{ item.name }} - {{ item.price }}
      </li>
    </ul>
    <br />
    <ul>
      <li v-for="(value, key, index) in user" :key="key">
        {{ key }}: {{ value }} ({{ index }})
      </li>
    </ul>
    <br />

    <ul>
      <template v-for="(user, index) in user">
        <li v-if="!user.isActive" :key="user.name">
          {{ user.name }}: {{ user.isActive ? "Active" : "Deactive" }} ({{
            index
          }})
        </li>
      </template>
    </ul>
  </div>
</template>
