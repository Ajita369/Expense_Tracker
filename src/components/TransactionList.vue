<template>
  <div>
    <h3 class="text-xl font-semibold text-gray-200 mb-4 mx-10">History</h3>
    <ul class="space-y-2">
      <li
        v-for="transaction in transactions"
        :key="transaction.id"
        :class="[
          'flex justify-between items-center p-4 bg-gray-200 rounded-lg shadow-sm mx-10',
          transaction.amount < 0 ? 'border-l-4 border-red-500' : 'border-l-4 border-green-500'
        ]"
      >
        <span>{{ transaction.text }}</span>
        <span class="font-bold"> &#x20B9{{ transaction.amount }}</span>
        <button
          class="bg-red-500 text-white px-2 py-1 rounded hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-red-600"
          @click="deleteTransaction(transaction.id)"
        >
          x
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(['transactionDeleted']);

const deleteTransaction = (id) => {
  emit('transactionDeleted', id);
};
</script>

<style scoped>
</style>
