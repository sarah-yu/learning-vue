<template>
  <div class='ui centered card'>
    <!--  show the to do item when we are not in editing mode -->
    <div class='content' v-show='!isEditing'>
      <div class='header'>
        {{toDo.title}}
      </div>

      <div class='meta'>
        {{toDo.project}}
      </div>

      <div class='extra content'>
        <span class='right floated edit icon' v-on:click='showForm'>
          <i class='edit icon'></i>
        </span>
        <span class='right floated trash icon' v-on:click='deleteToDo(toDo)'>
          <i class='trash icon'></i>
        </span>
      </div>
    </div><!-- .content -->

    <!--  show form when we are in editing mode -->
    <div class='content' v-show='isEditing'>
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model='toDo.title'>
        </div>
        <div class='field'>
          <label>Project</label>
          <input type='text' v-model='toDo.project'>
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click='hideForm'>Close X</button>
        </div>
      </div>
    </div>

    <!--  v-show: show complete or incomplete -->
    <div class='ui bottom attached green basic button' v-show='toDo.done && !isEditing' disabled>
      Completed
    </div>
    <div class='ui bottom attached red basic button' v-on:click='completeToDo(toDo)' v-show='!toDo.done && !isEditing'>
      Complete
    </div>
  </div>
</template>

<script>
export default {
  props: ['toDo'],
  data() {
    return {
      isEditing: false
    }
  },
  methods: {
    // emit delete-toDo event to the ToDoList parent component and pass the toDo item to be deleted
    deleteToDo(toDo) {
      this.$emit('delete-toDo', toDo)
    },
    completeToDo(toDo) {
      this.$emit('complete-toDo', toDo)
    },
    showForm() {
      this.isEditing = true
    },
    hideForm() {
      this.isEditing = false
    }
  }
}
</script>

<style>
</style>
