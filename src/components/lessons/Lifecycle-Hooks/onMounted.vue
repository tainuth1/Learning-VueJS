<script setup>
import { onBeforeMount, onBeforeUpdate, onMounted, onUpdated, ref } from "vue";
import onUnmounte from "./onUnmounte.vue";

const count = ref(0);

onBeforeMount(() => {
  console.log("onBeforemount: Before Component mount.");
});
onMounted(() => {
  console.log("onMounted: Component mounted.");
});
onBeforeUpdate(() => {
  console.log("onBeforeUpdate: Data is about to change.");
});
onUpdated(() => {
  console.log("onUpdated: Data has changed and DOM has been patched");
});
</script>
<template>
  <div class="h-[100vh] flex flex-col justify-center items-center">
    <onUnmounte v-if="count === 0" />
    <button
      @click="count++"
      class="px-5 py-2 rounded-lg text-white bg-blue-600 active:scale-[0.96]"
    >
      Count: {{ count }}
    </button>
  </div>
</template>
<!-- 
  onBeforeMount();
  onMounted();
  onBeforeUnmount();
  onUnmounted();
  onBeforeUpdate();
  onUpdated();
-->