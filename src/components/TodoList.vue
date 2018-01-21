<template lang="html">
  <div class="">
    <p>Completed Task: {{todos.filter(todo => {return todo.done == true}).length}}</p>
    <p>Pending Task: {{todos.filter(todo => {return todo.done == false}).length}}</p>

    <!-- passing the data to the todo component to render the todo list-->
    <todo v-on:delete-todo="deleteTodo"
     v-on:completeTodo="completeTodo"
     v-for="todo in todos" :key="todo.key" :todo="todo"></todo>
  </div>
</template>

<script>

import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
  },
};
</script>

<style lang="css">
</style>
