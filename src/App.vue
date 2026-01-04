<template>
  <div class="app">
    <h1>Task Tracker</h1>
    <TaskInput @add-task="addTask"/>
    <TaskList
      :tasks="tasks"
      @toggle-task="toggleTask"
      @delete-task="deleteTask"
    />

  </div>
  
  
</template>

<script setup>
  import { ref } from 'vue'
  import TaskInput from './components/TaskInput.vue';
import TaskList from './components/TaskList.vue';

  const tasks = ref([])

  function addTask(title) {
    tasks.value.push({
      id: Date.now(),
      title,
      done: false
    })
  }

  function toggleTask(id) {
    const task =  tasks.value.find(t => t.id === id)
    task.done = !task.done
  }

  function deleteTask(id){
    tasks.value = tasks.value.filter(t => t.id !== id )
  }


</script>
<style >
  .app {
    max-width: 500;
    margin: 40px auto;
    font-family: Arial, sans-serif;
  }
</style>