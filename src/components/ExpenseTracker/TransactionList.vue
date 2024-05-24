<script setup lang="ts"></script>

<template>
  <div>
    <h3>History</h3>
    <ul id="list" class="list">
      <li class="minus">
        New <span>22</span>
        <button class="delete-btn" @click="$emit('deleteExpenseRecord', '101')">x</button>
      </li>
      <li class="plus">
        New <span>22</span>
        <button class="delete-btn">x</button>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
