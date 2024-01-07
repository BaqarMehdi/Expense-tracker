<template>
    <h3>Add new Transaction</h3>
    <form id="form">
        <div class="form-control">
            <label for="text">Text</label>
            <input type="text" id="text" placeholder="Enter text ..." > 
        </div>
        <div class="form-control">
            <label for="amount">Amount <br>
            (Negative - Expense , Positive - income)
            </label>
            <input type="number" id="amount" placeholder="Enter amount ...">
        </div>
        <button class="btn" >Add Transaction</button>
    </form>
</template>
<!-- <script></script> -->