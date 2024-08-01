<template>
  <div class="flex justify-between bg-gray-200 p-4 rounded-lg shadow-md mt-5 mb-4 mx-10">
    <div class="text-center">
      <h4 class="text-sm font-semibold text-gray-600">Income</h4>
      <p class="text-lg font-bold text-green-500">+&#x20B9{{ income }}</p>
    </div>
    <div class="text-center">
      <h4 class="text-sm font-semibold text-gray-600">Expense</h4>
      <p class="text-lg font-bold text-red-500">-&#x20B9{{ expenses }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
});
</script>

<style scoped>
</style>
