<template>
  <div class="containe">
    <Header @show-task="showAddTask" title="All Tasks" :showTask="showTask" />
    <div v-show="showTask">
      <AddTask @add-task="addTask" />
    </div>

    <Tasks
      @double-reminder="doubleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data: function () {
    return {
      tasks: [],
      showTask: false,
    };
  },
  methods: {
    showAddTask() {
      this.showTask = !this.showTask;
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("Warning")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    doubleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    async fetchTasks() {
      const res = await fetch('http://localhost:5000/tasks');

      const data = await res.json();

      return data;
    },
  },
  async created() {
    this.tasks = await this.fetchTasks();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.btn {
  background-color: blue;
  color: white;
}
</style>
