<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <!-- Using for loop to show and class binding to show  -+ with ternary operator -->
    <li
      v-for="transaction in transactions"
      v-bind:key="transaction.id"
      :class="transaction.amount < 0 ? 'minus' : 'plus'"
    >
      {{ transaction.text }}<span>$ {{ transaction.amount }}</span>
      <button @click="deleteTransaction(transaction.id)" class="delete-btn">x</button>
    </li>
  </ul>
</template>

<script setup>
import { defineProps,defineEmits } from 'vue';

const emit = defineEmits('transactionDeleted')

// const props = defineProps
defineProps({
    transactions: {
        type: Array,
        required: true
    },
});

const deleteTransaction = (id) => { 
 emit('transactionDeleted', id)
}

</script>


<!-- scripting with composition api -->


<!-- export default {
  for option API
    data() {
      return {
        transactions: [
          { id: 1, text: "Flower", amount: -19.99 },
          { id: 2, text: "Salary", amount: 299.97 },
          { id: 3, text: "Book", amount: -10 },
          { id: 4, text: "Camera", amount: 150 },
        ],
      };
    },
  for composition API  old way
  setup() {
    Making a variable first
    const transactions = [
      { id: 1, text: "Flower", amount: -19.99 },
      { id: 2, text: "Salary", amount: 299.97 },
      { id: 3, text: "Book", amount: -10 },
      { id: 4, text: "Camera", amount: 150 },
    ];
    and then returnig
    return {
        transactions,
    }
  },
}; -->
<!-- <script setup></script>
</script> -->
