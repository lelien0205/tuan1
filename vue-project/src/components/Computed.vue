<script setup>
import { computed, reactive } from "vue";

const book = reactive({
  name: "Book 1",
  chapters: [],
});

const addChapter = () => {
  book.chapters.push("Chapter");
};

const isPublished = computed(() => {
  return book.chapters.length > 0 ? "Co" : "Khong";
});
</script>

<template>
  <div>
    <p id="count">Book name: {{ book.name }}</p>

    <p id="count">Đã xuất bản: {{ isPublished }}</p>
    <button @click="addChapter">Add Chapter</button>
  </div>
</template>
