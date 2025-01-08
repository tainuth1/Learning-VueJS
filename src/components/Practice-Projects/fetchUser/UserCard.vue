<script setup>
const props = defineProps({ user: Object });
</script>
<template>
  <div class="w-full h-full grid grid-cols-2 gap-3">
    <div class="col-span-1">
      <img
        class="w-full aspect-square object-cover rounded-lg border"
        :src="props.user.avatar_url"
        alt=""
      />
    </div>
    <div class="col-span-1">
      <h2 class="text-xl text-gray-700 font-semibold">{{ user.login }}</h2>
      <p class="text-sm text-gray-400">@{{ user.login }}</p>
      <button
        class="w-full bg-gradient-to-r from-indigo-500 to-blue-500 text-white font-bold py-2 px-4 rounded-md mt-2 hover:bg-indigo-600 hover:to-blue-600 transition ease-in-out duration-150"
      >
        View
      </button>
    </div>
  </div>
</template>
