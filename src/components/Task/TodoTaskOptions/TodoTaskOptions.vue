<template>
  <div class="row g-4 justify-content-center">    
    <div class="col-1 text-center">
      <todo-task-priority 
        :direction="1"
        @click="$emit('updatePriority', 1)"
      />
    </div>

    <div class="col-1 text-center">
      <todo-task-priority 
        :direction="-1"
        @click="$emit('updatePriority', -1)"
      />
    </div>

    <div class="col-1 text-center">
      <todo-task-edit 
        @enableEdit="propagateEdit"
      />
    </div>

    <div class="col-1 text-center">
      <todo-task-delete 
        @click="$emit('todoTaskDelete')"
      />
    </div>

  </div>
</template>

<script>
import TodoTaskDelete from "./TodoTaskDelete.vue";
import TodoTaskEdit from "./TodoTaskEdit.vue";
import TodoTaskPriority from "./TodoTaskPriority.vue";

export default {
  components: {
    TodoTaskDelete,
    TodoTaskEdit,
    TodoTaskPriority,
  },
  emits: ['updatePriority', 'propagateEdit', 'todoTaskDelete'],
  data() {
    return {
    };
  },
  methods: {
    propagateEdit(){
      this.$emit('propagateEdit')
    }
  },
};
</script>

<style>
</style>