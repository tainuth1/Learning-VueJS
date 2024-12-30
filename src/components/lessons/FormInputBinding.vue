<script setup>
import { ref } from "vue";

const inputText = ref("");
const onCheck = ref(false);
const multiCheck = ref([]);
const choseRadio = ref("");
const selectItem = ref("");
const multiSelect = ref([]);
const checkValue = ref("");

const removeFromChose = (remove) => {
  multiCheck.value = multiCheck.value.filter((item) => item != remove);
};
</script>
<template>
  <div class="w-[400px] m-auto p-3 rounded-lg shadow-xl">
    <div class="w-full">
      <h2 class="text-sm text-gray-500 my-1">You Typed: {{ inputText }}</h2>
      <input
        type="text"
        v-model="inputText"
        placeholder="Type something..."
        class="border w-full px-2 py-1 rounded-md focus:outline-blue-600"
      />
    </div>
    <hr class="my-2" />
    <div class="w-full">
      <input type="checkbox" v-model="onCheck" />
      <label for="">{{ onCheck }}</label>
    </div>
    <hr class="my-2" />
    <div class="w-full">
      <h2 class="text-sm text-gray-500 my-1">
        You chose: [<span
          @click="removeFromChose(check)"
          class="hover:underline cursor-pointer"
          v-for="(check, index) in multiCheck"
          :key="index"
          >"{{ check }}", </span
        >]
      </h2>

      <input type="checkbox" value="HTML" v-model="multiCheck" name="" id="" />
      <label for="" class="text-[13px]">HTML</label>

      <input
        type="checkbox"
        value="CSS"
        v-model="multiCheck"
        name=""
        id=""
        class="ml-3"
      />
      <label for="" class="text-[13px]">CSS</label>

      <input
        type="checkbox"
        value="Javascript"
        v-model="multiCheck"
        name=""
        id=""
        class="ml-3"
      />
      <label for="" class="text-[13px]">Javscript</label>
    </div>
    <hr class="my-2" />
    <div class="w-full">
      <h2 class="text-sm text-gray-500 my-1">You Chose: {{ choseRadio }}</h2>
      <input type="radio" value="One" id="one" v-model="choseRadio" />
      <label class="text-sm mr-5" for="">One</label>
      <input type="radio" value="Two" id="two" v-model="choseRadio" />
      <label class="text-sm" for="">Two</label>
    </div>
    <hr class="my-2" />
    <div class="w-full">
      <h2 class="text-sm text-gray-500 my-1">You Seleted: {{ selectItem }}</h2>
      <select
        v-model="selectItem"
        class="border text-sm w-full px-2 py-1 rounded-md focus:outline-blue-600"
      >
        <option disabled value="">Select Programming language</option>
        <option value="HTML">HTML</option>
        <option value="CSS">CSS</option>
        <option value="Javascript">Javascript</option>
      </select>
    </div>
    <hr class="my-2" />
    <div class="w-full">
      <h2 class="text-sm text-gray-500 my-1">
        You Seleted: [<span
          class="hover:underline cursor-pointer"
          v-for="(selected, index) in multiSelect"
          :key="index"
          >"{{ selected }}", </span
        >]
      </h2>
      <select
        v-model="multiSelect"
        multiple
        class="border text-sm w-full px-2 py-1 rounded-md focus:outline-blue-600"
      >
        <option value="HTML">HTML</option>
        <option value="CSS">CSS</option>
        <option value="Javascript">Javascript</option>
        <option value="Tailwind">Tailwind</option>
        <option value="Bootstrap">Bootstrap</option>
      </select>
    </div>
    <hr class="my-2" />
    <div class="w-full">
      <h2 class="text-sm text-gray-500 my-1">You Check: {{ checkValue }}</h2>
      <input
        type="checkbox"
        true-value="Real"
        false-value="Fake"
        v-model="checkValue"
      />
    </div>
    <hr class="my-2" />
  </div>
</template>
