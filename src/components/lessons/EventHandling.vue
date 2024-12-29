<script setup>
import { reactive, ref } from "vue";

const lists = ref([]);
const input = ref("");
const color = ref("#ffffff");
const err = ref(false);
const Background = reactive({
  backgroundColor: color,
});
const handleSubmit = (e) => {
  e.preventDefault();
  if (input.value.trim() != "") {
    lists.value = [...lists.value, input.value];
    err.value = false;
    input.value = "";
  } else {
    err.value = true;
  }
};
const hoverHandling = () => {
  color.value = "#000000";
};
const notHover = () => {
  color.value = "#ffffff";
};
const handleDelete = (title) =>
  (lists.value = lists.value.filter((list) => list !== title));
</script>
<template>
  <div class="w-full h-[100vh] p-5">
    <div
      :class="{ 'border-2 border-red-600': err }"
      :style="Background"
      class="w-[400px] m-auto p-3 rounded-lg shadow-lg"
    >
      <form class="flex gap-1">
        <input
          type="text"
          v-model="input"
          placeholder="Enter somthing...."
          class="border-2 rounded-md px-2 py-1"
        />
        <button
          @click="handleSubmit"
          @mouseover="hoverHandling"
          @mouseout="notHover"
          class="w-full px-3 bg-blue-600 text-white rounded-md active:scale-[0.97]"
        >
          Add
        </button>
      </form>
      <div class="flex items-center my-3">
        <input type="color" v-model="color" />
        Background Color: {{ color }}
      </div>
      <ul class="w-full pl-6">
        <li
          v-for="(list, index) in lists"
          :key="index"
          class="list-decimal text-lg text-gray-500 my-2 hover:underline cursor-pointer"
          @click="handleDelete(list)"
        >
          {{ list }}
        </li>
      </ul>
    </div>
  </div>
</template>
