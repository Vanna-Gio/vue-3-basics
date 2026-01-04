<template>
  <div class="app">
    <h1>Task Tracker</h1>
    <TaskInput @add-task="addTask"/>
    <TaskList
      :tasks="filteredTasks"
      @toggle-task="toggleTask"
      @delete-task="deleteTask"
      @update-task="updateTask"
    />

  </div>
  
  <div class="filters">
    <button @click="filter = 'all'">All</button>
    <button @click="filter = 'active'">Active</button>
    <button @click="filter = 'done'">Done</button>
    <p class="counter">
        Total: {{ totalCount }}
        | Active: {{ activeCount }}
        | Done: {{ doneCount }}
</p>

</div>


</template>

<script setup>
  import { ref,  computed } from 'vue'
  import TaskInput from './components/TaskInput.vue';
import TaskList from './components/TaskList.vue';
import { watch, onMounted } from 'vue';
const filter = ref('all')

const totalCount = computed(() => tasks.value.length)

const activeCount = computed(() => {
  return tasks.value.filter(t => !t.done).length
})

const doneCount = computed(() => {
  return tasks.value.filter(t => t.done).length
})

const filteredTasks = computed(() => {
  if (filter.value === 'active') {
    return tasks.value.filter(t => !t.done)
  }

  if (filter.value === 'done') {
    return tasks.value.filter(t => t.done)
  }

  return tasks.value
})

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

  onMounted(() => {
    const saved = localStorage.getItem('tasks')
    if (saved) {
      tasks.value = JSON.parse(saved)
    }
  })

  watch (tasks, (newTasks) => {
    localStorage.setItem('tasks', JSON.stringify(newTasks))
  }, { deep: true})
  
  function updateTask({id, title}) {
    const task = tasks.value.find(t => t.id === id)
    if(task){
      task.title = title
    }
  }
</script>
<style >
  .app {
    max-width: 500;
    margin: 40px auto;
    font-family: Arial, sans-serif;
  }
  .counter {
  margin: 10px 0;
  font-size: 14px;
  color: #555;
  
  }
 
  .filters button {
    margin-right: 8px;
  }

</style>