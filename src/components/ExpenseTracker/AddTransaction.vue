<script setup lang="ts">

import {nanoid} from "nanoid";
import {ref} from "vue";

const emit = defineEmits([
  'transactionSubmitted'
]);

const name = ref()
const amount = ref()

const addTransaction = () => {
  if (!name.value || !amount.value) {
    alert("Name and amount are required.")
    return
  }
  let payloadTransaction = {
    "id": nanoid(),
    "name": name.value,
    "amount": amount.value,
  }
  emit('transactionSubmitted', payloadTransaction);
  name.value = null
  amount.value = null
}
</script>

<template>
  <div>
    <div class="add-transaction-wrapper">
      <h3>Add new transaction</h3>
      <form id="form" @submit.prevent="addTransaction">
        <div class="form-control">
          <label for="text">Text</label>
          <input
              type="text"
              id="text"
              autocomplete="off"
              placeholder="Enter text..." v-model="name"/>
        </div>
        <div class="form-control">
          <label for="amount"
          >Amount <br/>
            (negative - expense, positive - income)</label
          >
          <input
              autocomplete="off"
              type="text"
              id="amount"
              placeholder="Enter amount..." v-model="amount"/>
        </div>
        <button class="add-transaction-btn">Add transaction</button>
      </form>
    </div>
  </div>
</template>

<style scoped></style>
