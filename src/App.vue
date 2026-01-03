<template>
  <h1>Vue 3 Basics</h1>
  <HelloWorld name="Vanna" @sayHello="handleHello"/>

  <!-- 6. Composition API (core vue 3 skills) -->
   <p>Count: {{ count }}</p>
   <button @click="increment">+</button>
   
   <p>User Name: {{ user.name }}, Age: {{ user.age }}</p>
</template>

<script>
import { ref, reactive } from 'vue';
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
  count.value ++;
  console.log('count is now ' + count.value);
  
}

const user = reactive({
  name: 'Vanna',
  age: 22
})
//directly reactive, no .value needed
user.name = 'Updated Vanna';
user.age = 23;


// Key rules:

// ref() → primitive values

// .value in JS, not in template
</script>
