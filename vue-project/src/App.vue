<script setup>
import { ref, reactive } from "vue";

const newTodo = ref("");
const editID = ref(null);

const todos = reactive([
  {
    id: 1,
    text: "Cong viec 1",
  },
  {
    id: 2,
    text: "Cong viec 2",
  },
]);

const addTodo = () => {
  if (newTodo.value.trim === "") return;
  const todo = {
    id: todos.length.id + 1,
    text: newTodo.value,
  };
  todos.push(todo);
  newTodo.value = "";
};

const selectTodo = (id) => {
  const todo = todos.find((todo) => todo.id === id);
  if (todo) {
    newTodo.value = todo.text;
    editID.value = id;
  }
};

const editTodo = () => {
  if (newTodo.value.trim() === "" || editID.value === null) return;
  const todo = todos.find((todo) => todo.id === editID.value);
  if (todo) {
    todo.text = newTodo.value;
  }
  newTodo.value = "";
  editID.value = "";
};

const deleteTodo = (id) => {
  const index = todos.findIndex((todo) => todo.id === id);
  if (index !== -1) {
    todos.splice(index, 1);
  }
};
</script>

<template>
  <div>
    <input type="text" v-model="newTodo" />
    <button @click="addTodo" :disabled="editID !== null">Add todo</button>
    <button @click="editTodo" :disabled="editID === null">Edit todo</button>
    <ul>
      <li v-for="todo in todos" :key="todos.id" @click="selectTodo(todo.id)">
        {{ todo.text }}
        <button @click="deleteTodo(todo.id)">Delete todo</button>
      </li>
    </ul>
  </div>
</template>

<!-- @keyup.enter="editTodo" -->
