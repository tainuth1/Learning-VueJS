<script setup>
import { ref } from "vue";
import Child from "./Child.vue";
const text = ref("Hello World");
const number = ref(100);

const Click = () => {
  console.log(`${number.value}, ${text.value}`);
};
const ClickGetData = (data) => {
  console.log(`Data : ${data}`);
};
</script>
<template>
  <Child
    :text="text"
    :number="number"
    :onClick="Click"
    :ClickGetData="ClickGetData"
  />
</template>
