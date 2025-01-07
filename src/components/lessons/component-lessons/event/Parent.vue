<script setup>
import { onUpdated, ref } from "vue";
import Child from "./Child.vue";

const buttons = ref([
  { id: 1, complete: false },
  { id: 2, complete: false },
  { id: 3, complete: false },
  { id: 4, complete: false },
  { id: 5, complete: false },
]);
const deleteButton = (id) => {
  buttons.value = buttons.value.filter((btn) => btn.id !== id);
};
const updateColor = (id) => {
  buttons.value = buttons.value.map((btn) => {
    return btn.id === id ? { ...btn, complete: !btn.complete } : btn;
  });
};
onUpdated(() => console.log(buttons.value ));
</script>
<template>
  <div class="w-full h-[100vh] flex justify-center gap-4 items-center">
    <Child
      v-for="btn in buttons"
      :key="btn.id"
      :button="btn"
      :updateColor="updateColor"
      @deleteButton="deleteButton"
      >{{ btn.id }}</Child
    >
  </div>
</template>
