<template>
  <ul 
    class="shadow-sm border border-2 bg-light rounded p-2 my-2 list-group list-group-flush"
    :class="{ 
              'border-danger': taskPriority===3, 
              'border-warning': taskPriority===2, 
              'border-secondary': taskPriority === 1 
            }"
  >
    <li class="list-group-item bg-light">
      <div class="form-check">
        <input 
          type="checkbox" 
          class="form-check-input"
          @click="checkBox"
        >
        <label 
          class="form-check-label"
          :class="{ 'text-decoration-line-through': checked === true }"
          v-if="!editEnabled"
        >
          {{ taskDescription }}
        </label>
          <input 
          type="text"
          v-if="editEnabled"
          v-model="taskDescription"
          @keyup.enter="editEnable" 
        >
        <todo-task-options-toggle 
          @toggled="enableOptions"
        />
      </div>
    </li>
    <li 
      class="list-group-item bg-light"
      v-if="showOptions"
    >
      <todo-task-options
        @propagateEdit="editEnable"
        @updatePriority="changePriority"
        @todoTaskDelete="$emit('deleteTask')"
      />
    </li>
  </ul>
</template>

<script>
import TodoTaskOptions from './TodoTaskOptions/TodoTaskOptions.vue'
import TodoTaskOptionsToggle from './TodoTaskOptions/TodoTaskOptionsToggle.vue'

export default {
  name: 'todo-task',
  props:['description', 'priority'],
  emits:['deleteTask'],
  components: {
    TodoTaskOptions,
    TodoTaskOptionsToggle
  },
  data() {
    return {
      taskPriority: this.priority,
      taskDescription: this.description,
      checked: false,
      editEnabled: false,
      showOptions: false
    }
  },
  methods: {
    changePriority(direction){
      if(this.taskPriority === 3 && direction >= 1) {return;}
      else if(this.taskPriority === 1 && direction <= 0) {return;}
      else {
        this.taskPriority += direction;
      }
    },
    checkBox() {
      this.checked = !this.checked;
    },
    editEnable() {
      this.editEnabled = !this.editEnabled;
    },
    enableOptions() {
      this.showOptions = !this.showOptions;
    }
  }
}
</script>

<style scoped>
  .form-check {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>