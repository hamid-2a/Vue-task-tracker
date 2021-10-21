<template>
  <div
    title="double click too add/remove reminder"
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.title }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
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

<style scope>
.fas {
  color: rgb(255, 0, 0);
  opacity: 0.4;
  padding: 5px;
}
.fas:hover {
  opacity: initial;
}
.task {
  background-color: #e9e9e9;
  margin: 10px 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 10px 5px 5px 10px;
  transition: padding 0.3s;
  transition: border-left 0.2s;
}
.task:hover {
  background-color: #e4e4e4;
  padding-left: 25px;
}
.task.reminder {
  border-left: 5px solid rgb(6, 196, 6);
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>