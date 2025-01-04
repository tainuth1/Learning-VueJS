<script setup>
defineProps(["data"]);
const emit = defineEmits(["decrease-font-size"]);
const decrease = () => {
  emit("decrease-font-size");
};
</script>
<template>
  <li class="text-sm text-gray-600 flex items-center">
    ID: {{ data.id }}, Name: {{ data.name }}
    <button
      @click="decrease"
      class="bg-blue-600 px-2 py-1 rounded-lg text-[11px] ml-5 active:scale-[0.98] text-white"
    >
      Decrease font size
    </button>
    <button
      @click="$emit('increase-font-size')"
      class="bg-blue-600 px-2 py-1 rounded-lg text-[11px] ml-5 active:scale-[0.98] text-white"
    >
      Increase font size
    </button>
  </li>
</template>
