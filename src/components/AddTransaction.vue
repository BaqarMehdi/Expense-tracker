<template>
    <h3>Add new Transaction</h3>
    <form id="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Text</label>
            <input type="text" id="text" v-model="text" placeholder="Enter text ..." > 
        </div>
        <div class="form-control">
            <label for="amount">Amount <br>
            (Negative - Expense , Positive - income)
            </label>
            <input type="text" id="amount" v-model="amount"  placeholder="Enter amount ...">
        </div>
        <button class="btn" >Add Transaction</button>
    </form>
</template>
<script setup>
import { ref } from 'vue';
import {useToast} from 'vue-toastification';
 
const text = ref('');
const amount = ref('')

const toast = useToast();

 const onSubmit = () => {
    if (!text.value || !amount.value) {
        toast.error ('Both fields must be filled');
        return;
    }
    console.log(text.value, amount.value)
    text.value = '';
    amount.value = '';
 };
</script>