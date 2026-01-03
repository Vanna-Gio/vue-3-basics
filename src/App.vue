<!-- ExampleComponent.vue -->
<template>
  <!-- Root element for the component -->
  <div class="example-component">
    <!-- Interpolation: display reactive data -->
    <h1>{{ message }}</h1>

    
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  setup() {
    const message = ref('Loading...')

    onMounted(()=>{
      // Runs after component is in the DOM
      message.value = 'Component has been mounted!';
      console.log('DOM is ready, you can interact with it now');

    });
    return { message}
    
  }
  
}
</script>

<style scoped>
.example-component h1 {
  color: #42b983;
}
</style>

