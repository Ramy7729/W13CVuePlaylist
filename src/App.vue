<!-- Using registered components (PageBody). -->
<template>
  <div id="app">
    <page-body/>
  </div>
</template>

<script>
// Importing the component.
import PageBody from './components/PageBody.vue'

export default {
  // Registering the component.
  name: 'App',
  components: {
    PageBody,
  }
}
</script>
    
<style>
body {
  background-color: #fbd2d7;
  background-image: url('./assets/som.jpg');
  background-size: cover;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
