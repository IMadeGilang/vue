<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<template>
    <p v-if="count < 10" class="text-yellow-500">Count is: {{ count }}</p>
</template>

<style scoped></style>