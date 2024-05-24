<script setup lang="ts">
defineProps({
  total: {
    required: true
  }
});
</script>

<template>
  <div>
    <h4>Your Balance</h4>
    <h1 id="balance">${{ total }}</h1>
  </div>
</template>

<style scoped></style>
