<template>
  <HeaderCom />
  <div class="container">
    <BalanceCom v-bind:total="+total" />
    <IncomeExpense v-bind:income="+income" v-bind:expenses="-expenses" />
    <!-- binding transactions function to transactions -->
    <TransactionList
      v-bind:transactions="transactions"
      @transactionDeleted="handleTransactionDeleted"
    />
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import HeaderCom from "./components/HeaderCom.vue";
import BalanceCom from "./components/BalanceCom.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
import { useToast } from "vue-toastification";
import { onMounted } from "vue";

const toast = useToast();

const transactions = ref([]);
// { id: 1, text: "Flower", amount: -19.99 },
// { id: 2, text: "Salary", amount: 299.97 },
// { id: 3, text: "Book", amount: -10 },
// { id: 4, text: "Camera", amount: 150 },

onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem("transactions"));
  if (savedTransactions) {
    transactions.value = savedTransactions;
  }
});
onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem('transactions'));

  if (savedTransactions) {
    transactions.value = savedTransactions;
  }
});
// console.log(transactions)

// get total
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});

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

const handleTransactionSubmitted = (transactionData) => {
  // console.log(transactionData)
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionData.text,
    amount: transactionData.amount,
  });

  savedTransactionsToLocalStorage()
  toast.success("Transaction added");
  console.log(generateUniqueId());
};
const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
};
const handleTransactionDeleted = (id) => {
  //  console.log(id)
  transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  );

  toast.success("Transaction Deleted");
};

// save in localStorage
const savedTransactionsToLocalStorage = () => {
  localStorage.setItem('transactions', JSON.stringify(transactions.value))
}

</script>

