<script setup>
import { ref } from 'vue'
const count = ref(0)

// import Paraf from './components/Paraf.vue'
// import IncrementButton from './components/IncrementButton.vue'
// import ReductionButton from './components/ReductionButton.vue'

function increment() {
  count.value++
}

function reduction() {
  count.value--
}

</script>

<template>
  <!-- <Paraf/>
  <IncrementButton/>
  <ReductionButton/> -->

  <p v-if="count < 10" class="text-yellow-500">Count is: {{ count }}</p>
  <br>
  <button @click="increment">Klik + 1</button>
  <br>
  <button @click="reduction">Klik - 1</button>

</template>

<style scoped>

</style>
