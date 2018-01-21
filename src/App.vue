<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <HelloWorld/> -->
    <todo-list :todos="todos"></todo-list>

    <create-todo v-on:create-todo="addTodo"></create-todo>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'

// import to-do component
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'App',
  components: {
    // HelloWorld
    TodoList,
    CreateTodo,
  },
  // data function avails data to the template
  data() {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false,
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
      }],
    };
  },
  methods: {
    addTodo(title, project) {
      this.todos.push({
        title,
        project,
        done: false,
      });
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
