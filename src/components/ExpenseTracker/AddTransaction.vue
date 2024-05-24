<script setup lang="ts">
const addTransaction = () => {
  alert('addTransaction')
}
</script>

<template>
  <div>
    <div class="add-transaction-wrapper">
      <h3>Add new transaction</h3>
      <form id="form" @submit.prevent="addTransaction">
        <div class="form-control">
          <label for="text">Text</label>
          <input type="text" id="text" autocomplete="off" placeholder="Enter text..." />
        </div>
        <div class="form-control">
          <label for="amount"
            >Amount <br />
            (negative - expense, positive - income)</label
          >
          <input autocomplete="off" type="text" id="amount" placeholder="Enter amount..." />
        </div>
        <button class="add-transaction-btn">Add transaction</button>
      </form>
    </div>
  </div>
</template>

<style scoped></style>
