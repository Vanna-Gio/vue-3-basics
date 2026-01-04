<template>
    <form @submit.prevent="submitTask">
        <input
            v-model="title"
            placeholder="New task"/>
        <button>Add</button>
    </form>
</template>
<script setup>
    import { ref } from 'vue'

    const title = ref('')
    const emit = defineEmits(['add-task'])

    function submitTask() {
        if (!title.value.trim()) return

        emit('add-task', title.value)
        title.value = ''
    }
</script>