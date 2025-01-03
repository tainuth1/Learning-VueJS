<script setup>
import { ref, watchEffect } from "vue";

const userInput = ref("");
let debounceTimeout = null;
watchEffect((onCleanup) => {
  if (!userInput.value.trim()) return;
  debounceTimeout = setTimeout(() => {
    console.log(`Fetched data: ${userInput.value}`);
  }, 500);
  onCleanup(() => clearTimeout(debounceTimeout));
});
</script>
<template>
  <button class="block ml-6 px-4 py-2 text-white bg-blue-600 rounded-lg">
    Click
  </button>
  <input
    type="text"
    placeholder="Enter something.."
    class="border px-4 py-2 my-2 rounded-lg ml-6"
    v-model="userInput"
  />
  <h2 class="ml-6">You Type: {{ userInput }}</h2>
</template>
