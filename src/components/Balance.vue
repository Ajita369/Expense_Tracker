<template>
  <div class="bg-gray-200 p-6 rounded-lg shadow-lg mt=5 mx-10">
    <h4 class="text-lg font-semibold text-gray-700">Your Balance</h4>
    <h1 class="text-3xl font-bold text-gray-900 mt-2"> &#x20B9{{ total }}</h1>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>

<style scoped>
</style>
