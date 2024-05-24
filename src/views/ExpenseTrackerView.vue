<template>
  <div class="container">
    <Header />
    <Balance />
    <IncomeExpenses />
    <TransactionList />
    <AddTransaction />
  </div>
</template>

<style></style>
<script setup lang="ts">
import Balance from '@/components/ExpenseTracker/Balance.vue'
import IncomeExpenses from '@/components/ExpenseTracker/IncomeExpenses.vue'
import TransactionList from '@/components/ExpenseTracker/TransactionList.vue'
import AddTransaction from '@/components/ExpenseTracker/AddTransaction.vue'
import Header from '@/components/ExpenseTracker/Header.vue'
</script>
