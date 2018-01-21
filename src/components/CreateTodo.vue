<template lang="html">
  <div class="ui basic content center aligned segment">
    <button type="button" name="button"
    class="ui basic button icon"
    v-on:click="openForm" v-show="!isCreating">
      <i class="plus icon"></i>
    </button>

    <div class="ui centered card" v-show="isCreating">
      <div class="content">
        <div class="ui form">
          <div class="field">
            <label>Title</label>
            <input type="text" v-model="titleText"
            ref="title" defaultValue="">
            <label>{{ titleText.length }}</label>
          </div><!-- end field -->
          <div class="field">
            <label>Project</label>
            <input type="text" v-model="projectText"
            ref="project" defaultValue="">
            <label>{{ projectText.length }}</label>
          </div><!-- end field-->
          <div class="ui two button attached buttons">
            <button type="button" class="ui basic blue button"
            v-on:click="sendForm">Create</button>
            <button type="button" class="ui basic red button"
            v-on:click="closeForm">Cancel</button>
          </div><!-- end ui two buttons-->
        </div><!-- end ui form -->
      </div><!-- end content-->
    </div>
    <!-- end ui centered card -->
  </div><!-- end div ui basic -->


</template>

<script>
export default {
  data() {
    return {
      titleText: '',
      projectText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project = this.projectText;

        // emit the event to the parent
        this.$emit('create-todo',
          title,
          project,
        );

        this.clearForm();
      }

      this.isCreating = false;
    },
    clearForm() {
      this.titleText = '';
      this.projectText = '';
    },
  },
};
</script>

<style lang="css">
</style>
