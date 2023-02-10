<template>
  <div class="containe">
    <Header title="All Tasks" />
    <div v-if="showTask">
      <AddTask @add-task="addTask"/>
    </div>
    
    <Tasks @double-reminder="doubleReminder" @delete-task="deleteTask" :tasks="tasks" />
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
    AddTask
  },
  data: function () {
    return {
      tasks: [],
      showTask: false
    };
  },
  methods: {
    addTask(task) {
     this.tasks = [...this.tasks, task]
    }, 
    deleteTask(id) {
      if (confirm("Warning")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    doubleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? 
      {...task, reminder: !task.reminder} : task)
    }

  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "task one..",
        month: "July",
        reminder: true,
      },
      {
        id: 2,
        text: "task two..",
        month: "May",
        reminder: false,
      },
      {
        id: 3,
        text: "task tree..",
        month: "June",
        reminder: true,
      },
    ];
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
