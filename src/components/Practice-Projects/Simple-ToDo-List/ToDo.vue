<script setup>
import { ref } from "vue";

const todos = ref([]);
const todoData = ref("");
const error = ref(false);
const isUpdate = ref(false);
const updateID = ref(null);

const handleSubmit = () => {
  if (isUpdate.value) {
    updateTodo();
  } else {
    addTodoList();
  }
};
const addTodoList = () => {
  const todoObject = { id: Date.now(), title: todoData.value };
  if (todoData.value.trim() != "") {
    todos.value = [...todos.value, todoObject];
    todoData.value = "";
    error.value = false;
  } else {
    error.value = true;
  }
};
const editTodo = (todo) => {
  todoData.value = todo.title;
  isUpdate.value = true;
  updateID.value = todo.id;
};
const updateTodo = () => {
  const filterUpdated = todos.value.map((item) =>
    item.id === updateID.value ? { ...item, title: todoData.value } : item
  );
  todos.value = filterUpdated;
  todoData.value = "";
  isUpdate.value = false;
  updateID.value = null;
};
const removeTodo = (id) => {
  const removeFiltered = todos.value.filter((item) => item.id !== id);
  todos.value = removeFiltered;
};
</script>
<template>
  <div class="w-[500px] m-auto p-4 border rounded-lg border-[#2B3040]">
    <form class="flex gap-2" @submit.prevent="handleSubmit">
      <input
        :class="{ 'border-red-600': error, 'border-[#2B3040]': !error }"
        class="bg-[#222630] w-full px-4 py-3 outline-none text-white rounded-lg border-2 transition-colors duration-100 border-solid focus:border-[#596A95]"
        placeholder="Enter you todo...."
        type="text"
        v-model="todoData"
        autocomplete="off"
      />
      <button
        type="submit"
        class="bg-[#222630] px-5 rounded-lg border-2 border-solid focus:border-[#596A95] border-[#2B3040] text-white"
      >
        {{ isUpdate ? "Update" : "Add" }}
      </button>
    </form>
    <div class="w-full flex flex-col gap-3 mt-3">
      <p
        v-if="todos.length == 0"
        class="text-lg my-4 text-center text-gray-400"
      >
        No Todo List Found!
      </p>
      <div
        class="bg-[#222630] w-full flex justify-between px-4 py-3 outline-none rounded-lg border-2 border-[#2B3040] text-gray-300"
        v-for="todo in todos"
        :key="todo.id"
      >
        {{ todo.title }}
        <div class="flex gap-2 items-center">
          <button
            @click="editTodo(todo)"
            class="bg-blue-600 px-4 py-1 rounded-md"
          >
            Edit
          </button>
          <button
            @click="removeTodo(todo.id)"
            class="bg-red-600 px-4 py-1 rounded-md"
          >
            Remove
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
body {
  background-color: #212121;
}
</style>
