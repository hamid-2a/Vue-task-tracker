<template>
  <header>
    <h1>{{ title }}</h1>

    <Button
      @btn-click="$emit('toggle-add-task')"
      :text="isShowAddTask ? 'Close' : 'Add Task'"
      :color="isShowAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "Header",
  props: {
    title: String,
    isShowAddTask: Boolean,
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
  margin-bottom: 20px;
}
</style>
