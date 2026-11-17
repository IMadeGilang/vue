<script setup>
import { ref } from 'vue'

// const msg = ref();

const message1 = ref('<<now you dont have any tasks. try to add some tasks>>')
const message2 = ref('<<hey you need to finish some tasks!!!!!!>>')


const props = defineProps(['tasks'])



</script>

<template>
    <h1>TO DO LIST</h1>
    <p>
        Here you can list all the tasks that you need to finish
    </p>
    <p v-if="props.tasks.length === 0">
        {{message1 }}
    </p>
    <p v-else>
        {{ message2}}
    </p>
</template>

<style scoped></style>