<script setup>
import { reactive, ref, watch, watchEffect } from "vue";

const count = ref(0);
const userInput = ref("");
const object = reactive({ name: "Tai Nuth", age: 19 });
watch(
  object,
  () => {
    console.log("Watch Object");
  }, {immediate: true}
);
watch(count, () => {
  console.log(`Watch count working: ${count.value}`);
});
watch(userInput, (newValue, oldValue) => {
  console.log(`New value: ${newValue}, Old Value: ${oldValue}`);
  count.value++;
});
watchEffect(() => {
  console.log(`watchEffect Working : ${count.value}.`);
});
// setInterval(() => {
//   object.age++;
// }, 1500);
</script>
<template>
  <button @click="count++" class="px-4 py-2 rounded-lg text-white bg-blue-600">
    Count: {{ count }}
  </button>
  <input
    type="text"
    placeholder="Enter something.."
    class="border px-4 py-2 rounded-lg ml-6"
    v-model="userInput"
  />
</template>
