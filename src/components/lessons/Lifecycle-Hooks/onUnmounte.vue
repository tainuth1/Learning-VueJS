<script setup>
import { onBeforeUnmount, onUnmounted } from "vue";

onUnmounted(() => {
  console.log("onUnmounted: Component unmounted from DOM.");
});
onBeforeUnmount(() => {
  console.log("onBeforeUnmount: Component is about to be removed");
});
</script>
<template>Hello</template>