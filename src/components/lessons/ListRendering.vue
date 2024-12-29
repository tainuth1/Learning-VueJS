<script setup>
import { reactive, ref } from "vue";
const myArray = reactive([10, 20, 30, 40, 50]);
const arrayObj = reactive([
  { name: "Tai Nuth", gender: "Male" },
  { name: "Phya Phya", gender: "Female" },
]);
const nestedArray = reactive([10, 20, [11, 22, 33, 44, 55], 40]);
const arrayChange = ref([10, 20, 30, 40, 50, 60, 70]);
arrayChange.value = arrayChange.value.filter((item) => item % 2 == 0);
</script>
<template>
  <div class="w-full grid grid-cols-5 gap-y-5">
    <ul class="block">
      <li v-for="arr in myArray" :key="arr" class="text-blue-600">{{ arr }}</li>
    </ul>
    <ul class="block">
      <li v-for="(arr, index) in myArray" :key="index" class="text-red-600">
        {{ index + 1 }} - {{ arr }}
      </li>
    </ul>
    <!-- Destructuring array object -->
    <ul class="block">
      <li
        v-for="({ name, gender }, index) in arrayObj"
        :key="index"
        class="text-[10px]"
      >
        {{ name }} - {{ gender }}
      </li>
    </ul>
    <!-- Nested array -->
    <ul class="col-span-2">
      <li v-for="(arr, key, index) in nestedArray" :key="index">
        {{ key }} - {{ arr }}
      </li>
    </ul>
    <!-- v-for with rage -->
    <ul class="">
      <li v-for="n in 6" :key="n">{{ n }}</li>
    </ul>

    <!-- Array change detection -->
    <ul>
      <li v-for="(arr, index) in arrayChange" :key="index">{{ arr }}</li>
    </ul>
  </div>
</template>
