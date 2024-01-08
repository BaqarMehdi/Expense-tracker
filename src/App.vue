<template>
  <HeaderCom />
  <div class="container">
    <BalanceCom v-bind:total="total" />
    <IncomeExpense v-bind:income="+income" v-bind:expenses="-expenses" />
    <!-- binding transactions function to transactions -->
    <TransactionList v-bind:transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import HeaderCom from "./components/HeaderCom.vue";
import BalanceCom from "./components/BalanceCom.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";

const transactions = ref([
  { id: 1, text: "Flower", amount: -19.99 },
  { id: 2, text: "Salary", amount: 299.97 },
  { id: 3, text: "Book", amount: -10 },
  { id: 4, text: "Camera", amount: 150 },
]);

// console.log(transactions)

// const total = computed(() => {
//   return transactions.value.reduce((acc, transaction) => {
//     return acc + transaction.amount;
//   }, 0);
// });

// get total
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});
// get income

// const income = computed (() => {
//   return transactions.value
//   .filter((transaction) =>
//     transaction.amount > 0
//   ).
//   reduce((acc, transaction) =>{
//     return acc + transaction.amount
//   }, 0).toFixed(2);
// });

// get expense

// const expense = computed (() => {
//   return transactions.value.filter((transaction) =>
//     transaction.amount < 0
//   ).
//   reduce((acc, transaction) =>{
//     return acc + transaction.amount
//   }, 0).toFixed(2);
// });

//
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

// Get expenses
const expenses = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

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
