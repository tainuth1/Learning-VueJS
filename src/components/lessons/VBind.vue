<script setup>
import { computed, reactive, ref } from "vue";
const isActive = ref(false);
const selectColor = ref("");
const inlineStyle = reactive({
  backgroundColor: selectColor,
  color: "white",
});
const change = () => {
  isActive.value = !isActive.value;
};
const color = ref("text-white");
const background = ref("bg-blue-600");
const isSpinning = computed(() => (!isActive.value ? "Start" : "Stop"));
</script>
<template>
  <div class="p-5">
    <h1
      :class="{ 'animate-spin': isActive }"
      class="text-2xl font-bold inline-block my-5 border-x-2 border-black px-3"
    >
      Hello World
    </h1>
    <button
      @click="change"
      class="block px-5 py-2 text-xl rounded-lg bg-blue-600 text-white"
    >
      {{ isSpinning }}
    </button>
    <h1
      :style="inlineStyle"
      class="text-2xl font-bold inline-block my-5 border-x-2 border-black px-3"
    >
      Hello World
    </h1>
    <input v-model="selectColor" type="color" />
    <input
      type="text"
      placeholder="Enter Color name...."
      v-model="selectColor"
      class="border-2 px-3 py-2 rounded-lg"
    />
    <h1 :class="[color, background]" class="text-2xl my-5 font-bold">
      Hello World
    </h1>
  </div>
</template>
