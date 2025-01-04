<script setup>
import { reactive, ref } from "vue";
import List from "./ChildComponent/List.vue";
const MyData = reactive([
  { id: 1, name: "Tai Nuth" },
  { id: 2, name: "Phya Phya" },
  { id: 3, name: "Phument CO" },
]);
const listFontSize = ref(20);
</script>
<template>
  <ul>
    <List
      :style="{ fontSize: listFontSize + 'px' }"
      v-for="data in MyData"
      :key="data.id"
      :data="data"
      @increase-font-size="listFontSize += 3"
      @decrease-font-size="listFontSize -= 3"
    />
  </ul>
</template>
