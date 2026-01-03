<!-- ExampleComponent.vue -->
<template>
  <!-- Root element for the component -->
  <div class="example-component">
    <!-- Interpolation: display reactive data -->
    <h1>{{ time }}</h1>

    
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'

export default {
  setup() {
   
    const time = ref(0);
    let intervalId ;

    onMounted(() => {
      intervalId = setInterval(() => {
        time.value++;

      }, 1000);
    });

    onUnmounted(() => {
      clearInterval(intervalId); //clean up timer
      console.log('Component unmounted, interval cleared.');
    });
    return { time };
    
    
  }
  
}
</script>

<style scoped>
.example-component h1 {
  color: #42b983;
}
</style>

 