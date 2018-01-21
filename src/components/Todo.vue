<template lang="html">
  <div class="">

    <div class="ui centered card">
    <!-- Todo shown when we are not in editing mode -->
      <div class="content" v-show="!isEditing">
        <div class="header">
          {{ todo.title }}
        </div>
        <div class="meta">
          {{ todo.project }}
        </div>

        <div class="extra content">
          <span class="right floated edit icon" v-on:click="showForm">
            <i class="edit icon"></i>
          </span>
          <!-- add the trash icon in below the edit icon in the template -->
          <span class="right floated trash icon" v-on:click="deleteTodo(todo)">
            <i class="trash icon"></i>
          </span>
        </div>
      </div><!-- end content-->

      <!-- the form is visible on editing mode only -->
      <div class="content" v-show="isEditing">
        <div class="ui form">
          <div class="field">
            <label>Title</label>
            <input type="text" v-model="todo.title">
          </div><!-- end field title-->
          <div class="field">
            <label>Project</label>
            <input type="text" v-model="todo.project">
          </div><!-- end field project -->
          <div class="ui two attached buttons">
            <button type="button" name="button" class="ui basic blue button"
            v-on:click="hideForm">Close X</button>
          </div><!-- end ui two attached buttons -->
        </div><!-- end ui form -->
      </div>

      <div class="ui bottom attached green basic button"
      v-show="!isEditing && todo.done">
        Completed
      </div>
      <div class="ui bottom attached red basic button"
      v-show="!isEditing && !todo.done">
        Pending
      </div>
    </div><!-- end centerd card -->

  </div>
</template>

<script>
export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    completeTodo(todo) {
      this.$emit('complete-todo', todo);
    },
    deleteTodo(todo) {
      this.$emit('delete-todo', todo);
    },
  },
};
</script>

<style lang="css">
</style>
