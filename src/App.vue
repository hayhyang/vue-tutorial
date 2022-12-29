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
  <ul class="list">
    <li v-for="todo in filteredTodo" :key="todo.id" :class="{done: todo.done}">
      <input type="checkbox" v-model="todo.done"/>
      {{todo.text}}
      <button @click="removeTodo(todo.id)">X</button>
    </li>
  </ul>

  <button @click="hideCompleted = !hideCompleted">Hide Completed</button>

  <p ref="p"></p>

  <p>Todo id: {{todoId}}</p>
  <button @click="todoId++">Fetch next todo</button>
  <p v-if="!todoData">...Loading</p>
  <pre v-else>{{todoData}}}</pre>
  <ChildComp />
</template>

<script>
import ChildComp from "./components/ChildComp.vue"
let id = 0;
export default {
  components: {
    ChildComp
  },
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
        {id: id++, text: 'Learn HTML', done: true},
        {id: id++, text: 'Learn Javascript', done: true},
        {id: id++, text: 'Learn Vue', done: false},
      ],
      newTodo: '',
      hideCompleted: false,
      todoId: 1,
      todoData: null,
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
    },
    async fetchData() {
      this.todoData = null
      const res = await fetch(`https://jsonplaceholder.typicode.com/todos/${this.todoId}`)
      this.todoData = await res.json()
    }
  },
  computed: {
    filteredTodo() {
      return this.hideCompleted ? this.todos.filter(el => !el.done) : this.todos

    }
  },
  mounted() {
    this.$refs.p.textContent = "Mounted!"
    this.fetchData()
  },
  watch: {
    todoId() {
      this.fetchData(0)
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
.list li.done {
  text-decoration: line-through;
}
</style>
