<template>
  <div class="container">
    
    <div class="col-lg-6 col-md-10 mx-auto">
      <div class="row text-center my-4">
        <h1>TODO APP</h1>
        <p> A very simple todo app.</p>
      </div>

      <task-input
        @addTodoTask="appendTask"
      />

      <todo-task-container
        :tasks="tasks"
      />
    </div>
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
