<script setup>
// import place
import { ref } from 'vue' 
import TodoListHeader from './components/TodoListHeader.vue'
//between bellow this comment is the new code for the local storage

//take saved tasks from localstorage
const savedtasks = localStorage.getItem('tasks')
const saveddone = localStorage.getItem('done')

let tasks 
let done

// check if the savedtasks(the localstorage) is empty
if(savedtasks !== null){
  tasks = ref(JSON.parse(savedtasks))
}else{
  tasks = ref([])
}
// the same thing but for the done list
if(saveddone !== null){
  done = ref(JSON.parse(saveddone))
}else{
  done = ref([])
}

// a function to refresh/update the localstorage or to add/delete something to the localstorage
function savetasks(){  
  localStorage.setItem('tasks', JSON.stringify(tasks.value))
  localStorage.setItem('done', JSON.stringify(done.value))
}
// above is the localstorage new code replacing the const tasks and const done

// bellow this comment is the variable i use when not using localstorage. the localsorage counterpart is the "let tasks en let done"
// const tasks = ref(['blabla', 'blabla2'])  // first iteration without the localstorage
// const done = ref([])

// tis is the variable to the new tasks that the user write in the input form element
const newtask = ref('')

// this function is a function to add everything that user write to the tasks variable
function addtask(){
  if(newtask.value !== ''){
    tasks.value.push(newtask.value)
    newtask.value = ''
    savetasks()
  }
}

// this function is a function to move a task from backlogs to the done list
function movetodone(index){
  done.value.push(tasks.value.splice(index,1)[0]) // to remove the "[]" in the list
  savetasks()
}

// a delete function
function deletetask(indexv2){
  done.value.splice(indexv2,1)
  savetasks()
}

// a fail attaempt to make delete everything button

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

// maybe the problem is using @submit.prevent


</script>

<template>
  <div class="grid grid-cols-2 gap-6 max-w-4xl mx-auto p-6">

      <!--bellow this comment is a div for a big paragraf at the top of the website--> 
      <div class="col-span-2 bg-slate-800 text-white p-8 rounded-xl">
        <TodoListHeader v-bind:tasks="tasks"/><br> <!--component is here--> 
        <h1 
          class="text-2xl font-bold mb-4">
          input your tasks bellow
        </h1>
        <form @submit.prevent="addtask" class="flex gap-3">
        <input type="text" v-model="newtask" 
          class="flex-1 p-3 rounded-lg text-yellow" 
          placeholder="Enter a task...">
        <button type="submit" class="bg-blue-500 hover:bg-blue-600 px-5 rounded-lg">add</button>
      </form>
      </div>
      
      <!--backlogs list-->
      <div class="bg-slate-100 p-6 rounded-xl">
      <p class="text-xl font-bold mb-4">Backlogs</p><br>
      <ul>
        <li v-for="(value, index) in tasks" v-bind:key="index" class="bg-white p-3 rounded-lg mb-3 flex justify-between">
          {{ value }}
          <button @click="movetodone(index)" class="bg-blue-500 text-white px-3 py-1 rounded-lg">move to done</button>
          <!-- <p v-if="done !== ''">add something</p> -->
        </li>
      </ul>
      </div>
      
      <!--done list-->
      <div class="bg-slate-100 p-6 rounded-xl">
      <p class="text-xl font-bold mb-4">done</p><br>
      <ul>
        <li v-for="(value,indexv2) in done" v-bind:key="indexv2" class="bg-white p-3 rounded-lg mb-3 flex justify-between">
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