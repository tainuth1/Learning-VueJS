<script setup>
const props = defineProps({ button: Object, updateColor: Function });
const emit = defineEmits(["deleteButton"]);
const sentId = (id) => {
  emit("deleteButton", id);
};
</script>
<template>
  <div class="border-2 flex items-center gap-2 border-gray-400 rounded-lg p-2">
    <button
      class="btn"
      :class="{
        'bg-red-600': !button.complete,
        'bg-blue-600': button.complete,
      }"
      @click="sentId(button.id)"
    >
      Delete
    </button>
    <button
      class="btn"
      :class="{
        'bg-red-600': !button.complete,
        'bg-blue-600': button.complete,
      }"
      @click="updateColor(button.id)"
    >
      Change Color
    </button>
  </div>
</template>
