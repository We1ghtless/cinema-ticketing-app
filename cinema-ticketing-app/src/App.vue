<template>
  <div class="">
    <Form />
  </div>
</template>

<script>
import Form from './components/form.vue'
export default {
  name: 'App',
  components: {
    'Form': Form,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: auto;
  margin-top: 60px;
  max-width: 300px;
}
</style>
