<script setup>
import { reactive, ref } from "vue";

const color = ref("");
const array = reactive([10, 20, 30, 40, 50]);
const handleSubmit = (e) => {
  e.preventDefault();
  console.log(color);
};
</script>
<template>
  <form
    @submit="handleSubmit"
    :class="{ 'bg-red-600': color === 'red' }"
    class="w-52 m-auto bg-gray-400 shadow-md p-4"
  >
    <input
      type="text"
      v-model="color"
      placeholder="Enter color name....."
      class="w-full border-2 px-3 py-2 rounded-lg"
    />
    <button
      type="submit"
      class="bg-blue-600 text-white px-5 py-2 rounded-lg mt-3 active:scale-[0.98]"
    >
      Submit
    </button>
    <h1
      v-if="color === 'red'"
      :style="{ color: color }"
      class="text-sm mt-2 text-white"
    >
      You enter the correct color.
    </h1>
    <br />
    <h1 v-for="arr in array" :key="arr" class="inline-block mr-4 mt-2 drop-shadow-lg text-white">
      Hello
    </h1>
  </form>
</template>
