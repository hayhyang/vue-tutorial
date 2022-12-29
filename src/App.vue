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

  <form @submit.prevent="addTodo">
    <input type="text" v-model="newTodo"/>
    <button type="submit">입력</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">{{todo.text}}
      <button @click="removeTodo(todo.id)">X</button>
    </li>

  </ul>

</template>

<script>

let id = 0;
export default {
  data() {
    return {
      message: 'Hello world',
      counter: {
        count: 0
      },
      titleClass: 'title',
      text: '',
      awesome: true,
      todos: [
        {id: id++, text: 'Learn HTML'},
        {id: id++, text: 'Learn Javascript'},
        {id: id++, text: 'Learn Vue'},
      ],
      newTodo: ''
    }
  },
  methods: {
    increment() {
      this.counter.count++
    },
    toggle() {
      this.awesome = !this.awesome
    },
    addTodo() {
      this.todos = [...this.todos, {id: id++, text: this.newTodo}];
      this.newTodo = ''
    },
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
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
