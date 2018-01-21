<template lang="html">
  <div class="">
    <p>Completed Task: {{todos.filter(todo => {return todo.done == true}).length}}</p>
    <p>Pending Task: {{todos.filter(todo => {return todo.done == false}).length}}</p>

    <!-- passing the data to the todo component to render the todo list-->
    <todo v-on:delete-todo="deleteTodo"
     v-on:completeTodo="completeTodo"
     v-for="(todo, index) in todos"
     :index="index"
     :key="todo.id"
     :todo="todo"></todo>
  </div>
</template>

<script>
import sweetalert from 'sweetalert';

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
      sweetalert('Success!', 'To-Do completed!', 'success');
    },
    deleteTodo(todo) {
      sweetalert({
        title: 'Are you sure?',
        text: 'Do you have the required grasp to delete this To-Do?',
        icon: 'warning',
        buttons: {
          cancel: {
            text: 'Cancel',
            visible: true,
            value: null,
            closeModal: true,
          },
          confirm: {
            text: 'Yes, delete it!',
            value: true,
            closeModal: true,
          },
        },
      })
        .then((willDelete) => {
          if (willDelete) {
            const todoIndex = this.todos.indexOf(todo);
            this.todos.splice(todoIndex, 1);
            sweetalert('Deleted!', 'Your To-Do has been deleted.', 'success');
          } else {
            sweetalert('Your To Do was kept on the App');
          }
        });
    },
  },
};
</script>

<style lang="css">
</style>
