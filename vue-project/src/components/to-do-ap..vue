<script setup>
import { ref, reactive } from "vue";

// Ô nhập liệu
const newTodo = ref("");

// Danh sách công việc
const todos = reactive([
  { id: 1, text: "Learn Vue.js" },
  { id: 2, text: "Build a todo app" },
]);

// Lưu ID của công việc đang được sửa
const editingId = ref(null);

// Thêm công việc
const addTodo = () => {
  if (newTodo.value.trim() === "") return;
  const todo = {
    id: todos.length > 0 ? todos[todos.length - 1].id + 1 : 1,
    text: newTodo.value,
  };
  todos.push(todo);
  newTodo.value = "";
};

// Chọn công việc để sửa
const selectTodo = (id) => {
  const todo = todos.find((todo) => todo.id === id);
  if (todo) {
    newTodo.value = todo.text; // Hiển thị nội dung công việc trong ô nhập
    editingId.value = id; // Lưu ID của công việc đang sửa
  }
};

// Sửa công việc
const editTodo = () => {
  if (editingId.value === null || newTodo.value.trim() === "") return;
  const todo = todos.find((todo) => todo.id === editingId.value);
  if (todo) {
    todo.text = newTodo.value; // Cập nhật nội dung công việc
  }
  newTodo.value = ""; // Xóa ô nhập
  editingId.value = null; // Xóa trạng thái sửa
};

// Xóa công việc
const deleteTodo = (id) => {
  const index = todos.findIndex((todo) => todo.id === id);
  if (index !== -1) {
    todos.splice(index, 1);
  }
};
</script>

<template>
  <div>
    <!-- Ô nhập liệu -->
    <input type="text" v-model="newTodo" placeholder="Nhập công việc" />
    <div>
      <!-- Nút thêm -->
      <button @click="addTodo" :disabled="editingId !== null">Thêm</button>
      <!-- Nút sửa -->
      <button @click="editTodo" :disabled="editingId === null">Sửa</button>
    </div>

    <!-- Danh sách công việc -->
    <ul>
      <li v-for="todo in todos" :key="todo.id" @click="selectTodo(todo.id)">
        {{ todo.text }}
        <!-- Nút xóa -->
        <button @click.stop="deleteTodo(todo.id)">Xóa</button>
      </li>
    </ul>
  </div>
</template>

<!-- @keyup.enter="editTodo" -->
