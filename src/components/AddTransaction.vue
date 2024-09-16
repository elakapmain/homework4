<script setup>
    import { ref, defineEmits } from 'vue';

    const text = ref('')
    const amount = ref('')  //  Is string, but will be parsed later on

    const emit = defineEmits([
        'transactionSubmitted'
    ])    //  Event handler

    const onSubmit = () => {
        const transactionData = {
            text: text.value,
            amount: parseFloat(amount.value)    //  Parse text 
        }

        emit('transactionSubmitted', transactionData)

        text.value = ''
        amount.value = ''
    }
</script>

<template>
    <h3>Add a new transaction</h3>
    <form id="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Enter transaction</label>
            <input type="text" id="text" v-model="text" placeholder="Enter transaction...">
        </div>
        <div class="form-control">
            <label for="amount">Enter transaction amount</label>
            <input type="text" id="amount" v-model="amount" placeholder="Enter negative value for expenses...">
        </div>
        <button class="btn">Add Transaction</button>
    </form>
</template>