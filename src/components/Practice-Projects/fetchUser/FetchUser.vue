<script setup>
import { ref } from "vue";
import UserCard from "./UserCard.vue";
let API_URL = "https://api.github.com/users";
const searchQuery = ref("");
const user = ref(null);
const notFound = ref(false);
const isLoading = ref(false);
const fetchUser = async (username) => {
  isLoading.value = true;
  try {
    const res = await fetch(`${API_URL}/${username}`, {
      headers: {
        Authorization: "token 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",
      },
    });
    if (!res.ok) {
      throw new Error("Failed to fetch data from API");
    }
    user.value = await res.json();
    notFound.value = false;
  } catch (error) {
    user.value = null;
    notFound.value = true;
  } finally {
    isLoading.value = false;
  }
};
const handleSubmit = () => {
  if (searchQuery.value.trim() !== "") {
    fetchUser(searchQuery.value);
  } else {
    alert("Plex Pjol User Name Hx Bro!!");
  }
};
</script>
<template>
  <div class="flex flex-col items-center justify-center light">
    <div class="w-full max-w-md bg-white rounded-lg shadow-md p-6">
      <h2 class="text-2xl font-bold text-gray-800 mb-4">Search Github User</h2>

      <form class="flex flex-col" @submit.prevent="handleSubmit">
        <input
          type="text"
          v-model="searchQuery"
          class="bg-gray-100 text-gray-800 border-0 rounded-md p-2 mb-4 focus:bg-gray-200 focus:outline-none focus:ring-1 focus:ring-blue-500 transition ease-in-out duration-150"
          placeholder="Enter github username"
        />

        <button
          type="submit"
          class="bg-gradient-to-r from-indigo-500 to-blue-500 text-white font-bold py-2 px-4 rounded-md mt-2 hover:bg-indigo-600 hover:to-blue-600 transition ease-in-out duration-150"
        >
          Find User
        </button>
      </form>

      <div class="mt-4 flex flex-col gap-5">
        <!-- Loading state -->
        <div v-if="isLoading" class="w-full flex justify-center">
          <div
            class="w-10 h-10 border-4 border-t-blue-500 border-gray-300 rounded-full animate-spin"
          ></div>
        </div>

        <!-- User found -->
        <UserCard v-else-if="user" :user="user" />

        <!-- User not found -->
        <p
          v-else-if="notFound"
          class="text-lg text-center text-gray-600 hover:underline"
        >
          Search not found
        </p>

        <!-- Default state -->
        <p v-else class="text-lg text-center text-gray-600 hover:underline">
          No User
        </p>
      </div>
    </div>
  </div>
</template>
