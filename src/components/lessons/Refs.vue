<script setup>
import { onMounted, ref } from "vue";
import RefsChildComponent from "./RefsChildComponent.vue";
const autoRef = ref(null);
const inputRef = ref(null);
const chooseFile = ref(null);
const childComponentRef = ref(null);
const imageChose = ref("");
const focusInput = () => {
  inputRef.value.focus();
};
const focusFile = () => {
  chooseFile.value.click();
};
const changeChildState = () => {
  childComponentRef.value.toggleState();
};
const handleFile = (e) => {
  imageChose.value = e.target.files[0];
  console.log(imageChose.value);
};
// Will learning this soon
onMounted(() => {
  autoRef.value.focus();
});
</script>
<template>
  <input
    type="text"
    ref="autoRef"
    placeholder="Start Typing it will show here.."
    class="border w-60 px-4 py-2 my-2 rounded-lg ml-6"
  />
  <input
    type="text"
    ref="inputRef"
    placeholder="Enter something.."
    class="border px-4 py-2 my-2 rounded-lg ml-6"
  />
  <button
    @click="focusInput"
    class="block ml-6 px-4 py-2 text-white bg-blue-600 rounded-lg"
  >
    Focus Input
  </button>
  <input
    type="file"
    ref="chooseFile"
    @change="handleFile"
    class="focus:outline-2 focus:outline-blue-600 w-56 border px-4 py-2 my-2 rounded-lg ml-6"
  />
  <button
    @click="focusFile"
    class="inline-block ml-6 px-4 py-2 text-white bg-blue-600 rounded-lg"
  >
    Select File
  </button>
  <img
    :src="imageChose"
    class="inline-block"
    width="50px"
    height="50px"
    alt=""
  />

  <div class="my-4 ml-6">
    <RefsChildComponent ref="childComponentRef" />
  </div>
  <button
    @click="changeChildState"
    class="block ml-6 px-4 py-2 text-white bg-blue-600 rounded-lg"
  >
    Toggle State
  </button>
</template>
