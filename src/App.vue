<template>
  <div id="app">
    <h1>{{ msg }}</h1>

    <form v-on:submit.prevent="submitHandler">
      <input v-model="newTodoValue" type="text" required>
      <button type="submit">Add Todo</button>
    </form>

    <h2>Todos ({{ todosAmount }})</h2>

    <TodoList v-bind:todos="todos" v-on:updateTodo="updateTodo"/>
  </div>
</template>

<script>
import TodoList from './components/TodoList'

let i = 1;

export default {
  name: 'app',
  components: {
    TodoList,
  },
  data() {
    return {
      msg: 'Hello World!!!!',
      newTodoValue: '',
      todos: [
        {
          id: i++,
          title: 'My first todo',
          done: false,
        },
        {
          id: i++,
          title: 'My second todo',
          done: false,
        }
      ]
    };
  },
  computed: {
    todosAmount() {
      return this.todos.length;
    }
  },
  methods: {
    submitHandler() {
      this.todos.push({
        id: i++,
        title: this.newTodoValue,
        done: false,
      });
      this.newTodoValue = '';
    },
    doneHandler(todo) {
      // console.log(todo); // eslint-disable-line
      todo.done = true;
    },
    updateTodo() {
      
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 30px;

  h1 {
    font-size: 40px;
  }
}

.is-done {
  color: green;
}
</style>
