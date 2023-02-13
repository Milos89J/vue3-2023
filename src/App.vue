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
    async addTask(task) {
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
          
        },
        body: JSON.stringify(task),
      });
      const data = await res.json()
      this.tasks = [...this.tasks, ];
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
      const res = await fetch("api/tasks");

      const data = await res.json();

      return data;
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`);

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
