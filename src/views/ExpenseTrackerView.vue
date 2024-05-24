<template>
  <div class="container">
    <Header />
    <Balance />
    <IncomeExpenses />
    <TransactionList :transactions="transactions" />
    <<AddTransaction @transactionSubmitted="transactionSubmitted"/>
  </div>
</template>

<style></style>
<script setup lang="ts">
import Balance from '@/components/ExpenseTracker/Balance.vue'
import IncomeExpenses from '@/components/ExpenseTracker/IncomeExpenses.vue'
import TransactionList from '@/components/ExpenseTracker/TransactionList.vue'
import AddTransaction from '@/components/ExpenseTracker/AddTransaction.vue'
import Header from '@/components/ExpenseTracker/Header.vue'
import {nanoid} from 'nanoid'
import {computed, ref} from "vue";

let transactions = ref([
  {
    'id': nanoid(),
    'name': 'Pay Check',
    'amount': '400'
  },
  {
    'id': nanoid(),
    'name': 'Hello',
    'amount': '-40'
  }
]);


function transactionSubmitted(data: any) {
  if (data && data.hasOwnProperty('id') && data.hasOwnProperty('name') && data.hasOwnProperty('amount')) {
    transactions.value.push(data);
    return true;
  }

  alert('Error: Transaction');
  return false;
}



</script>
