<template>
  <div
    @click="$emit('double-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h2>{{ task.text }}</h2>
    <i @click="$emit('delete-task', id)" class="fas fa-times"></i>
    <p>{{ task.month }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
};
</script>

<style scoped>
.task {
  background-color: bisque;
  margin: 10px;
  padding: 3px;
  cursor: pointer;
}
.task.reminder {
  border-left: 4px solid blue;
}
.fas {
  color: blue;
}
</style>