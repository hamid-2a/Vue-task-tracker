<template>
  <div class="container">
    <Header
      title="Task Tracker"
      @toggle-add-task="toggleAddTask"
      :isShowAddTask="isShowAddTask"
    />

    <div v-show="isShowAddTask" class="add-task">
      <AddTask @add-task="addTask" />
    </div>

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
    Tasks,
    AddTask,
  },

  data() {
    return {
      tasks: [],
      isShowAddTask: false,
    };
  },

  methods: {
    addTask(newTask) {
      this.tasks = [newTask, ...this.tasks];
    },

    toggleAddTask() {
      this.isShowAddTask = !this.isShowAddTask;
    },

    deleteTask(id) {
      if (confirm("Are you sure to delete this task?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },

    toggleReminder(id) {
      this.tasks = this.tasks.map((item) =>
        item.id === id ? { ...item, reminder: !item.reminder } : item
      );
    },
  },

  created() {
    this.tasks = [
      {
        id: 1,
        title: "selected or you",
        day: "2021-10-12",
        reminder: true,
      },
      {
        id: 2,
        title: "who can order for easy and services",
        day: "2021-10-02",
        reminder: false,
      },
      {
        id: 3,
        title: "shun the pardon less",
        day: "2021-08-23",
        reminder: false,
      },
      {
        id: 4,
        title: "and further times",
        day: "2021-04-22",
        reminder: true,
      },
      {
        id: 5,
        title: "as if to obtain because they provide for him",
        day: "2021-03-28",
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
  background-image: url("~@/assets/backgrounds/bg-1.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
  transition: background-image 0.2s;
}
.container {
  background-color: #ffffff;
  width: 550px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid rgb(179, 179, 179);
  padding: 30px;
  border-radius: 5px;
  transition: all 0.3s;
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

@media screen and (max-width: 1900px) {
  body {
    background-image: url("~@/assets/backgrounds/bg-2.jpg");
  }
}

@media screen and (max-width: 1200px) {
  body {
    background-image: url("~@/assets/backgrounds/bg-3.jpg");
  }
}

@media screen and (max-width: 850px) {
  .container {
    width: 98%;
  }
}
</style>
