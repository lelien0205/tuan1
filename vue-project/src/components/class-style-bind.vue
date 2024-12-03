<script setup>
import { computed, reactive, ref } from "vue";

const color = ref("red");
const background = ref("blue");
const fontSize = ref(30);

const styleObject = reactive({
  border: "none",
  borderRadius: "6px",
});

const isActive = ref(true);
const hasError = ref(true);

const classObject = computed(() => ({
  active: isActive.value && hasError.value,
  "has-error": hasError.value,
}));

const changeActive = () => {
  isActive.value = !isActive.value;
};
</script>
<template>
  <div>
    <button @click="changeActive" class="button" :class="classObject">
      {{ isActive ? "Active" : "Deactive" }}
    </button>
    <br />
    <br />
    <button
      :style="[
        {
          color,
          background,
          fontSize: fontSize + 'px',
        },
        styleObject,
      ]"
    >
      Xin chao
    </button>
  </div>
</template>

<style>
.button {
  border: none;
  background: #ede9fe;
  color: #8b5cf6;
  padding: 10px 14px;
  border-radius: 6px;
  cursor: pointer;
  &:hover {
    background: #c7d2fe;
  }
}
.active {
  color: #ede9fe;
  background: #8b5cf6;
  &:hover {
    background: #818cf8;
  }
}

.has-error {
  color: #ede9fe;
  background: #ef4444;
  &:hover {
    background: #818cf8;
  }
}
</style>
