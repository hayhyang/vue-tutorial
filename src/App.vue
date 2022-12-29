<template>
  <div>{{ message }}</div>
  <p>Count is: {{counter.count}}</p>
  <h1 :class="titleClass">Make me red</h1>
  <button @click="increment">{{counter.count}}</button>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello world',
      counter: {
        count: 0
      },
      titleClass: 'title'
    }
  },
  methods: {
    increment() {
      this.counter.count++
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

.title {
  color: red;
}
</style>
