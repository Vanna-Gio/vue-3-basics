<template>
  <h1>Vue 3 Basics</h1>
  <HelloWorld name="Vanna" @sayHello="handleHello"/>
</template>

<script>
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
</script>
