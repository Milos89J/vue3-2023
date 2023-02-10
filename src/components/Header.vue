<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      @show-task="$emit('show-task')"
      :text="showTask ? 'Close' : 'Add'"
      :color="showTask ? 'red' : 'blue'"
    />
  </header>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  props: {
    title: String,
    showTask: Boolean,
  },
  components: {
    Button,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 25px;
}
</style>