<template>
  <main>
    <div class="appWrapper">
      <div class="appHeader">
        <h1>Task Tracker App</h1>
        <Button
          @toggle-add-task="toggleAddTask"
          :title="!showTask ? 'Add Task' : 'Close'"
          :bgcolor="!showTask ? 'green' : ' red'"
          :showAddTask="showTask"
        />
      </div>
      <div v-if="showTask"><AddTask @add-task="addTask" /></div>
      <Tasks
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask"
        :tasks="tasks"
      />
    </div>
  </main>
</template>

<script >
import Button from "./../components/Button.vue";
import Tasks from "./../components/Tasks.vue";
import AddTask from "./../components/AddTask.vue";

export default {
  name: "HomePage",
  props: {},

  components: {
    Button,
    Tasks,
    AddTask,
  },
  data() {
    return { tasks: [], showTask: false };
  },
  methods: {
    async addTask(task) {
      const res = await fetch("http://localhost:5000/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });

      const data = await res.json();

      this.tasks = [...this.tasks, data];
    },
    async deleteTask(id) {
      console.log("task id in source component" + id);

      if (confirm("Are you sure")) {
        const res = await fetch(`http://localhost:5000/tasks/${id}`, {
          method: "DELETE",
          headers: {
            "Content-type": "application/json",
          },
        });
        res.status === 200
          ? (this.tasks = this.tasks.filter((task) => task.id !== id))
          : alert("error deleting task");
      }
    },

    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id);

      const updateTask = { ...taskToToggle, reminder: !taskToToggle.reminder };

      const res = await fetch(`http://localhost:5000/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updateTask),
      });

      const data = await res.json();

      console.log("id for toggle is  " + id);
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !data.reminder } : task
      );
    },
    toggleAddTask() {
      this.showTask = !this.showTask;
    },

    async fetchTasks() {
      const res = await fetch("http://localhost:5000/tasks");

      const data = res.json();
      return data;
    },
    async fetchTask(id) {
      const res = await fetch(`http://localhost:5000/tasks/${id}`);
      const data = await res.json();
      return data;
    },
  },
  async created() {
    this.tasks = await this.fetchTasks();
  },
};
</script>



<style scoped>
.appWrapper {
  display: flex;
  width: 50%;
  justify-content: center;
  gap: 10%;
  background-color: azure;
  align-self: center;
  flex-direction: column;
  padding: 30px;
  border-radius: 5px;
}
.appHeader {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
main {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  align-content: flex-start;
  justify-content: flex-start;
}
</style>
