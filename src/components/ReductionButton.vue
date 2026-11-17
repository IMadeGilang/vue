<script setup>
// import { ref } from 'vue'
// const count = ref(0)

function reduction() {
  count.value--
}
</script>

<template>
    <br>
    <button v-on:click="reduction">Klik - 1</button>
</template>

<style scoped></style>