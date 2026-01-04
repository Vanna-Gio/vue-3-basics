<template>
    <ul>
        <li v-for="task in tasks" :key="task.id">
            <span 
                :style="{ textDecoration: task.done ? 'line-through' : 'none'}"
                @click="toggle(task.id)"
            >
                {{ task.title }}
            </span>
            <button @click="remove(task.id)">×</button>
        </li>
    </ul>
   
</template>

<script setup>
    defineProps({
        tasks: Array
    })

    const emit = defineEmits(['toggle-task', 'delete-task'])

    function toggle(id){
        emit('toggle-task', id)
    }

    function remove(id){
        emit('delete-task', id)
    }

</script>