<script setup lang="ts">

import { nanoid } from 'nanoid'

const transactionData = [
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

<template>
  <div>
    <h3>History</h3>
    <ul id="list" class="list">
      <li
        v-for="transaction in transactionData"
        :key="transaction.id"
        :data-nanoid="transaction.id"
        :class="(Number(transaction.amount) < 0) ? 'minus' : 'plus'">
        {{ transaction?.name || 'N/A' }} <span>{{ Number(transaction?.amount) || '-' }}</span>
        <button class="delete-btn" @click="$emit('deleteExpenseRecord', transaction.id)">x</button>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
