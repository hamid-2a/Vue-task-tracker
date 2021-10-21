<template>
  <form @submit="handleSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="title" name="title" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="date"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

//------------------------------
<script>
export default {
  name: "AddTask",

  data() {
    return {
      title: "",
      day: "",
      reminder: false,
    };
  },

  methods: {
    handleSubmit(e) {
      e.preventDefault();

      if (!this.title || !this.day) alert("Please fill all fields");

      const newTask = {
        id: Math.floor(Math.random() * 10000),
        title: this.title,
        day: this.day,
        reminder: this.reminder,
      };

      this.$emit("add-task", newTask);

      (this.title = ""), (this.day = ""), (this.reminder = false);
    },
  },
};
</script>

//-------------------------------
<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
}
.form-control-check input {
  height: 20px;
  width: 30px;
}

/* .form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
} */
</style>