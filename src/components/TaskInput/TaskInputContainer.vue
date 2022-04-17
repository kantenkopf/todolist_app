<template>
  <div class="row mb-4 p-3 rounded shadow-sm bg-white">
      <input 
        type="text" 
        class="col mx-1" v-model="taskDescription" placeholder="My Next Task"
        @keyup.enter="clearInput()"
      >
      <div class="col-1 mx-1 text-center">
        <task-add-button 
        @click="clearInput()"
      />
      </div>
  </div>
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