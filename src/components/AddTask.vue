<template>
  <form @submit="onSubmit" class="add-form">
    <div class="div form-control">
      <label>Task</label>
      <input type="text" v-model="task" name="text" placeholder="task" />
    </div>
    <div class="div form-control">
      <label>Month</label>
      <input type="text" v-model="month" name="month" placeholder="new text" />
    </div>
    <div class="div form-control form-control-check">
      <label>Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>
    <input type="submit" value="save" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data: function () {
    return {
      text: "",
      month: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();

      const newTask = {
        id: Math.floor(Math.random() * 100),
        text: this.text,
        month: this.month,
        reminder: this.reminder
      }
      this.$emit('add-task', newTask)


      this.text = '',
      this.month = '',
      this.reminder = false
    },
  },
};
</script>

<style scoped>
</style>
