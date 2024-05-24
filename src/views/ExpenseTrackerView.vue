<template>
  <div class="container">
    <Header/>
    <Balance :total="total"/>
    <IncomeExpenses :expense="expense" :income="income"/>
    <TransactionList :transactions="transactions" @deleteExpense="deleteExpenseFn"/>
    <AddTransaction @transactionSubmitted="transactionSubmitted"/>
  </div>
</template>

<style></style>
<script setup lang="ts">
import Balance from '@/components/ExpenseTracker/Balance.vue'
import IncomeExpenses from '@/components/ExpenseTracker/IncomeExpenses.vue'
import TransactionList from '@/components/ExpenseTracker/TransactionList.vue'
import AddTransaction from '@/components/ExpenseTracker/AddTransaction.vue'
import Header from '@/components/ExpenseTracker/Header.vue'
import {computed, onMounted, ref} from "vue";

const localStorageKey = "_expense_data";

let transactions = ref([]);

onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem(localStorageKey))
  if (savedTransactions) {
    transactions.value = savedTransactions
  }
});

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + Number(transaction.amount);
  }, 0).toFixed(2);
})

const income = computed(() => {
  return transactions.value
      .filter((transaction) => {
        return Number(transaction.amount) > 0
      })
      .reduce((acc, transaction) => {
        return acc + Number(transaction.amount)
      }, 0).toFixed(2);
});

const expense = computed(() => {
  return transactions.value
      .filter((transaction) => {
        return Number(transaction.amount) < 0
      })
      .reduce((acc, transaction) => {
        return acc + Number(transaction.amount)
      }, 0).toFixed(2);
});

function transactionSubmitted(data: any) {
  if (data && data.hasOwnProperty('id') && data.hasOwnProperty('name') && data.hasOwnProperty('amount')) {
    transactions.value.push(data);
    saveTransactionToLocalStorage()
    return true;
  }
  alert('Error: Transaction');

  return false;
}

const saveTransactionToLocalStorage = () => {
  localStorage.setItem(localStorageKey, JSON.stringify(transactions.value))
}

function deleteExpenseFn(id: string) {
  transactions.value = transactions.value.filter((item) => {
    return item.id != id;
  });

  saveTransactionToLocalStorage()
}

</script>
