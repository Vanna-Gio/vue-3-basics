<template>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      
      <!-- EDIT MODE -->
      <template v-if="editingId === task.id">
        <input
          v-model="editTitle"
          @keyup.enter="save(task.id)"
          @blur="save(task.id)"
          autofocus
        />
      </template>

      <!-- VIEW MODE -->
      <template v-else>
        <span
          :style="{ textDecoration: task.done ? 'line-through' : 'none' }"
          @click="toggle(task.id)"
          @dblclick="startEdit(task)"
        >
          {{ task.title }}
        </span>
        <button @click="remove(task.id)">x</button>
      </template>

    </li>
  </ul>
</template>


<script setup>
    import { ref } from 'vue'
    const editingId = ref(null)
    const editTitle =ref('')

    defineProps({
        tasks: Array
    })

    const emit = defineEmits([
    'toggle-task', 
    'delete-task',
    'update-task'
    ])
    function startEdit(task) {
        editingId.value =task.id
        editTitle.value = task.title
    }
    function save(id) {
        if(!editTitle.value.trim()) return

        emit ('update-task', {
            id,
            title: editTitle.value
        })
    }
    function toggle(id){
        emit('toggle-task', id)
    }

    function remove(id){
        emit('delete-task', id)
    }

</script>