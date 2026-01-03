<template>
  <div>
    <!-- 4. Props (parent -> child) -->
    <h2>Hello, {{ name }}!</h2>
    <p>Welcome to your Vue.js application.</p>
    <!-- 5. Emits (child -> parent) -->
     <button @click="sendMessage">click Me</button>
  </div>
</template>
<script>
  export default {
    props: {
      name: String
    },
    emits: ['sayHello'],
    methods: {
      sendMessage(){
        this.$emit('sayHello', 'Hello from child component!')
      }
    }
  }
</script>