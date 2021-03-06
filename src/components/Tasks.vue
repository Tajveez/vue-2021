<template>
  <div v-for="task in tasks" :key="task.id">
    <!-- <h3>{{ task.text }}</h3> -->
    <Task :task="task" />
  </div>
</template>

<script>
import Task from "./Task";
export default {
  name: "Tasks",
  components: {
    Task,
  },
  props: {
    tasks: Array,
  },
};
</script>

<style></style>
