<template>
  <div class="container">
      <div class="row text-center my-4">
        <h1>TODO APP</h1>
        <p> A very simple todo app.</p>
      </div>
      
      <task-input
        class="row col-sm-12 col-md-11 col-lg-9 col-xxl-8 bg-white shadow-sm rounded mx-auto p-3 px-md-5 mb-4"
        @addTodoTask="appendTask"
      />

      <todo-task-container
        class="row col-md-11 col-lg-9 col-xxl-8 bg-white shadow-sm rounded mx-auto p-3 px-md-5"
        :tasks="tasks"
      />
  </div>
</template>

<script>
import TodoTaskContainer from './components/Task/TodoTaskContainer.vue';
import TaskInput from './components/TaskInput/TaskInputContainer.vue';

export default {
  name: 'App',
  components: {
    TodoTaskContainer,
    TaskInput
  },
  data() {
    return {
      tasks: [{
                description: "First Task",
                priority: 3
              }, 
              {
                description: "Second Task",
                priority: 2
              }, 
              {
                description: "Third Task",
                priority: 1
              }]
    }
  },
  methods: {
    appendTask(description) {
      this.tasks.push({description: description, priority: 1});
    }
  }
}
</script>

<style>
  body {
    background-color: #d3d3d3;
  }
</style>
