<script setup lang="ts">

defineProps({
  transactions: {
    type: Array,
    required: true,
    default: () => []
  }
})
</script>

<template>
  <div>
    <h3>History</h3>
    <ul id="list" class="list">
      <li
        v-for="transaction in transactions"
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
