<template>
  <form
    @submit.prevent
    class="container justify-content-center"
  >
      <input 
        type="text" 
        class="form-control col-10" v-model="taskDescription" placeholder="My Next Task"
        @keyup.enter="clearInput()"
      >
      <div class="col-1 text-center">
        <task-add-button 
          @click="clearInput()"
        />
      </div>
  </form>
</template>

<script>
import TaskAddButton from './TaskAddButton.vue'

export default {
  components: {
    TaskAddButton,
  },
  data() {
    return {
      taskDescription: ""
    }
  },
  methods: {
    clearInput() {
      this.$emit('addTodoTask', this.taskDescription)
      this.taskDescription = "";
    }
  }
}
</script>

<style>

</style>