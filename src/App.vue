<template>
  <div class="p-5">
    <h1 class="mb-5 text-3xl font-bold text-blue-600">Count: {{ count }}</h1>
    <h1 class="mb-5 text-3xl font-bold text-blue-600">
      Watch Count: {{ watchCount }}
    </h1>
    <button
      v-on:click="Increment"
      class="px-5 py-2 bg-blue-600 text-white rounded-md active:scale-[0.99]"
    >
      Update
    </button>
    <h1 v-if="isVisible" class="my-5 text-3xl font-bold text-blue-600">
      Visible
    </h1>
    <h1 v-else class="my-5 text-3xl font-bold text-red-600">Hidden</h1>
    <hr class="my-2" />
    <input
      type="text"
      placeholder="Enter somthing..."
      v-model="userInput"
      class="border-2 px-3 py-2 rounded-lg"
    />
    <h1 class="my-5 text-xl font-bold text-blue-600 mr-5">
      Show from Input : {{ capitalUserInput }}
    </h1>
    <hr class="my-2" />
    <span
      v-for="(arr, index) in array"
      :key="index"
      class="my-5 text-3xl font-bold text-blue-600 mr-5"
    >
      {{ arr }}
    </span>
  </div>
</template>
<script setup>
import { computed, reactive, ref, watch } from "vue";
const userInput = ref("Hello");
const capitalUserInput = computed(() => {
  return userInput.value.toUpperCase();
});
const isVisible = ref(true);
const count = ref(0);
const watchCount = ref(0);
const array = reactive(["HTML", "CSS", "Tailwind", "JavaScript", "ReactJS"]);
const Increment = () => {
  count.value++;
  isVisible.value = !isVisible.value;
};
watch([count], () => {
  watchCount.value++;
});
</script>
