<script setup>
const props = defineProps({
  text: String,
  number: Number,
  onClick: Function,
  ClickGetData: Function,
});
</script>
<template>
  <div class="w-[500px] m-auto">
    <h1>{{ text }} - {{ number }}</h1>
    <button
      @click="onClick"
      class="px-5 py-2 rounded-lg bg-blue-600 text-white"
    >
      Click Event
    </button>
    <button
      @click="ClickGetData('Hello World')"
      class="px-5 py-2 rounded-lg bg-blue-600 text-white"
    >
      Click Parameter
    </button>
  </div>
</template>
