<!-- ExampleComponent.vue -->
<template>
  <!-- Root element for the component -->
  <div class="example-component">
    <!-- Interpolation: display reactive data -->
    <h1>{{ message }}</h1>

    <!-- Conditional rendering -->
    <p v-if="isVisible">This text is visible</p>
    <p v-else>This text is hidden</p>

    <!-- List rendering -->
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.name }}</li>
    </ul>

    <!-- Event handling -->
    <button @click="handleClick">Click Me</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const message = ref('Hello, Vue 3!')
    const isVisible = ref(true)
    const items = ref([
      { id: 1, name: 'Item One' },
      { id: 2, name: 'Item Two' },
      { id: 3, name: 'Item Three' }
    ])

    const handleClick = () => {
      isVisible.value = !isVisible.value
    }

    return { message, isVisible, items, handleClick }
  }
}
</script>

<style scoped>
.example-component h1 {
  color: #42b983;
}
</style>

