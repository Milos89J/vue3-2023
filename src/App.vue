<template>
  <div class="containe">
    <Header title="All Tasks"/>
  </div>
</template>

<script>
import Header from './components/Header';
export default {
  name: "App",
  components: {
    Header,
  },
  data: function() {
    return {
      tasks: []
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
        text: "task one..",
        month: "May",
        reminder: false,
      },
      {
        id: 3,
        text: "task one..",
        month: "June",
        reminder: true,
      },
    ]
  }
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
  color:white;
}
</style>
