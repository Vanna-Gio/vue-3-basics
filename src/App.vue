<template>
  <h1>Vue 3 Basics</h1>
  <HelloWorld name="Vanna" @sayHello="handleHello"/>

  <!-- 6. Composition API (core vue 3 skills) -->
   <p>Count: {{ count }}</p>
   <button @click="increment">+</button>
</template>

<script>
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'

export default {
  components: {
    HelloWorld
  },
  methods: {
    handleHello(message){
      alert(message)
    }
  }
}
// Composition API
const count = ref(0);
function increment(){
  count.value++;
}

// Key rules:

// ref() → primitive values

// .value in JS, not in template
</script>
