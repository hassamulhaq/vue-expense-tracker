<template>
  <div class="container">
    <Header />
    <Balance />
    <IncomeExpenses />
    <TransactionList :transactions="transactions" />
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
import { nanoid } from 'nanoid'

const transactions = [
  {
    'id': nanoid(),
    'name': 'Pay Check',
    'amount': '400'
  },
  {
    'id': nanoid(),
    'name': 'Lunch',
    'amount': '-77'
  },
  {
    'id': nanoid(),
    'name': 'Fuel',
    'amount': '-10'
  },
  {
    'id': nanoid(),
    'name': 'A4tech Mouse',
    'amount': '-20'
  },
  {
    'id': nanoid(),
    'name': 'Bond',
    'amount': '90'
  }
]
</script>
