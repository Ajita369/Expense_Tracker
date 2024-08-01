<template>
  <div class="bg-gray-200 p-6 rounded-lg shadow-lg mt-6 mx-10">
  <h3 class="text-lg font-semibold text-gray-700 mb-4">Add New Transaction</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="mb-4">
      <label for="text" class="block text-gray-600">Text</label>
      <input type="text" id="text"  class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:ring focus:ring-blue-500 focus:border-blue-500" 
       placeholder="Enter text..." v-model="text" />
    </div>
    <div class="mb-4">
      <label for="amount" class="block text-gray-600"
        >Amount <br />
        (negative - expense, positive - income)</label
      >
      <input
        type="text"
        id="amount"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:ring focus:ring-blue-500 focus:border-blue-500"
        placeholder="Enter amount..."
        v-model="amount"
      />
    </div>
    <button class="w-full bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-600">
      Add transaction</button>
  </form>
  </div>
</template>

<script setup>
import { useToast } from 'vue-toastification';
import { ref } from 'vue';

const text = ref('');
const amount = ref('');

const toast = useToast();

const emit = defineEmits(['transactionSubmitted']);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    toast.error('Both fields must be filled.');
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit('transactionSubmitted', transactionData);

  text.value = '';
  amount.value = '';
};
</script>