<template>
  <div>{{ message }}</div>
  <p>Count is: {{counter.count}}</p>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello world',
      counter: {
        count: 0
      }
    }
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
  margin-top: 60px;
}
</style>
