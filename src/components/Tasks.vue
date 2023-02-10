<template>
  <div v-for="task in tasks" :key="task.id">
    <Task @double-reminder="$emit('double-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task"/>
</div>
  
</template>

<script>
import Task from './Task';
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task
  },
  emits: ['delete-task', 'double-reminder'],
};
</script>

<style scoped>
</style>
