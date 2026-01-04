<template>
  <div class="app">
    <h1>Task Tracker</h1>
    <TaskInput @add-task="addTask"/>
  </div>
</template>

<script setup>
  import { ref } from 'vue'
  import TaskInput from './components/TaskInput.vue';

  const tasks = ref([])

  function addTask(title) {
    tasks.value.push({
      id: Date.now(),
      title,
      done: false
    })
  }


</script>
<style >
  .app {
    max-width: 500;
    margin: 40px auto;
    font-family: Arial, sans-serif;
  }
</style>