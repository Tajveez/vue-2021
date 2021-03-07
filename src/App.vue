<template>
  <div class="container">
    <Header
      @toggle-form="toggleForm"
      title="Task Tracker"
      :btnText="btnText"
      :btnColor="btnColor"
    />
    <AddTask v-if="showForm" @add-task="addTask" />
    <Tasks
      @toggle-reminder="toggleReminder"
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
    AddTask,
    Tasks,
  },
  data() {
    return {
      tasks: [],
      showForm: false,
      btnText: "Add Task",
      btnColor: "green",
    };
  },
  methods: {
    toggleForm() {
      this.showForm = !this.showForm;
      if (this.showForm) {
        this.btnText = "Close Form";
        this.btnColor = "orange";
      } else {
        this.btnText = "Add Task";
        this.btnColor = "green";
      }
    },
    deleteTask(id) {
      if (confirm("Are you Sure?"))
        this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    toggleReminder(id) {
      console.log(id);
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    addTask(newTask) {
      this.tasks = [newTask, ...this.tasks];
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor Appointment",
        day: "March 8th at 2:00PM",
        reminder: true,
      },
      {
        id: 2,
        text: "Walima",
        day: "March 7th at 5:00PM",
        reminder: true,
      },
      {
        id: 3,
        text: "Shopping",
        day: "March 9th at 2:00PM",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
