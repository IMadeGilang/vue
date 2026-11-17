<script setup>
// import { ref } from 'vue'
// const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
    <br>
    <button v-on:click="increment">Klik + 1</button>
</template>

<style scoped></style>