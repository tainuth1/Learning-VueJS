<script setup>
import { ref, defineExpose } from "vue";

const isActive = ref(false);
const toggleState = () => {
  isActive.value = !isActive.value;
};
defineExpose({ toggleState });
</script>
<template>
  <h1 class="text-2xl text-blue-600 font-bold">
    {{ isActive ? "Active" : "Inative" }}
  </h1>
</template>
