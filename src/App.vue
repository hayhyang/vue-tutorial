<template>
  <div>{{ message }}</div>
  <p>Count is: {{counter.count}}</p>
  <h1 :class="titleClass">Make me red</h1>
  <button @click="increment">{{counter.count}}</button>
  <input v-model="text" placeholder="Type here" />
  <p>{{text}}</p>

  <button @click="toggle">toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no T.T</h1>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello world',
      counter: {
        count: 0
      },
      titleClass: 'title',
      text: '',
      awesome: true
    }
  },
  methods: {
    increment() {
      this.counter.count++
    },
    toggle() {
      this.awesome = !this.awesome
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
