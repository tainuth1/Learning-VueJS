<script setup>
import { ref } from "vue";
const props = defineProps(["order", "bg"]);
console.log(props.order);
const count = ref(0);
const handleClick = () => {
  count.value++;
};
</script>
<template>
  <button
    @click="handleClick"
    :class="bg"
    class="px-5 py-2 font-semibold text-white rounded-full transition-all hover:scale-[1.05] active:scale-100 outline-blue-600"
  >
    Click BTN {{ order }} to Count: {{ count }}
  </button>
</template>
