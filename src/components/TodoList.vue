<template>
  <ul>
    <li
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:class="{ 'is-done': todo.done }"  
    >
      {{ todo.title }}
      <template v-if="!todo.done">
        <button v-on:click="doneHandler(todo)">DONE!</button>
      </template>
      <span v-else>YAY</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: [
    'todos'
  ],
  methods: {
    doneHandler(todo) {
      this.$emit('updateTodo', {
        action: 'done',
        todo,
      })
    }
  }
}
</script>
