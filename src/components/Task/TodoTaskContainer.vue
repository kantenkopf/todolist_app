<template>
    <div>
        <todo-task
            v-for="(task, index) in todoTasks"
            :description="task.description"
            :priority="task.priority"
            :key="JSON.stringify(task)"
            @deleteTask="removeTodoTask(index)"
        />
    </div>
</template>

<script>
import TodoTask from './TodoTask.vue'

export default {
    components: {
        TodoTask
    },
    props: ['tasks'],
    data() {
        return {
            todoTasks: this.tasks,
        }
    },
    methods: {
        removeTodoTask(index) {
            this.todoTasks.splice(index, 1)
        }
    }
}
</script>

<style>

</style>