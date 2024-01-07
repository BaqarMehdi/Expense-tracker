<template>
  <HeaderCom />
  <div class="container">
    <BalanceCom />
    <IncomeExpense />
    <!-- binding transactions function to transactions -->
    <TransactionList v-bind:transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<script setup>
import {ref} from 'vue'
import HeaderCom from "./components/HeaderCom.vue";
import BalanceCom from "./components/BalanceCom.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";

const transactions = ref( [
  { id: 1, text: "Flower", amount: -19.99 },
  { id: 2, text: "Salary", amount: 299.97 },
  { id: 3, text: "Book", amount: -10 },
  { id: 4, text: "Camera", amount: 150 },
]);

// export default {
//   name: 'App',
//   components: {
//     HeaderCom,
//     BalanceCom,
//     IncomeExpense,
//     TransactionList,
//     AddTransaction
//   }
// }
</script>

<style>
/* @import url(./assets/style.css); */
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
