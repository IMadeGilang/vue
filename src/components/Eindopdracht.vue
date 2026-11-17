<script setup>
import { ref } from 'vue' 
import TodoListHeader from './components/TodoListHeader.vue'
//between bellow this comment is the new code for the local storage
const savedtasks = localStorage.getItem('tasks')
const saveddone = localStorage.getItem('done')

let tasks 
let done

if(savedtasks !== null){
  tasks = ref(JSON.parse(savedtasks))
}else{
  tasks = ref([])
}

if(saveddone !== null){
  done = ref(JSON.parse(saveddone))
}else{
  done = ref([])
}

function savetasks(){  // to refresh the local storage
  localStorage.setItem('tasks', JSON.stringify(tasks.value))
  localStorage.setItem('done', JSON.stringify(done.value))
}
// above is the localstorage new code replacing the const tasks and const done
const newtask = ref('')

// const tasks = ref(['blabla', 'blabla2'])  // first iteration without the localstorage
// const done = ref([])

function addtask(){
  if(newtask.value !== ''){
    tasks.value.push(newtask.value)
    newtask.value = ''
    savetasks()
  }
}

function movetodone(index){
  done.value.push(tasks.value.splice(index,1)[0])
  savetasks()
}

function deletetask(indexv2){
  done.value.splice(indexv2,1)
  savetasks()
}


// function clearstorage(){
//   localStorage.clear();
//   savetasks()
// }

// function lsclear(){
//   done.value = ref([])
//   tasks.value = ref([])
//   localStorage.removeItem(tasks)
//   localStorage.removeItem(done)
//   // localStorage.clear()
//   // savetasks()

// }



</script>

<template>
  <div class="grid grid-cols-2 gap-6 max-w-4xl mx-auto p-6">
    <div class="col-span-2 bg-slate-800 text-white p-8 rounded-xl">
  <TodoListHeader v-bind:tasks="tasks"/><br>
    <h1 class="text-2xl font-bold mb-4">input your tasks bellow</h1>
    <form @submit.prevent="addtask" class="flex gap-3">
      <input type="text" v-model="newtask" class="flex-1 p-3 rounded-lg text-yellow" placeholder="Enter a task...">
      <button type="submit" class="bg-blue-500 hover:bg-blue-600 px-5 rounded-lg">add</button>
    </form>
    </div>

    <div class="bg-slate-100 p-6 rounded-xl">
    <p class="text-xl font-bold mb-4">to do list</p><br>
    <ul>
      <li v-for="(value, index) in tasks" :key="index" class="bg-white p-3 rounded-lg mb-3 flex justify-between">
        {{ value }}
        <button @click="movetodone(index)" class="bg-blue-500 text-white px-3 py-1 rounded-lg">move to done</button>
        <!-- <p v-if="done !== ''">add something</p> -->
      </li>
    </ul>
    </div>

    <div class="bg-slate-100 p-6 rounded-xl">
    <p class="text-xl font-bold mb-4">done</p><br>
    <ul>
      <li v-for="(value,indexv2) in done" :key="indexv2" class="bg-white p-3 rounded-lg mb-3 flex justify-between">
        {{ value }}
        <button @click="deletetask(indexv2)" class="bg-red-500 text-white px-3 py-1 rounded-lg">delete</button>
      </li>
    </ul>
    </div>

    <!-- <button @click="lsclear">remove local storage</button> -->
  </div>
    
</template>

<style scoped>

</style>