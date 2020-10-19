<template>
  <h2>Option API</h2>
  <ul class="todos">
    <li v-for="(task, index) in todos" :key="index">
      <span
        @click="toggleTaskStatus(task)"
        :class="{ completed: task.completed }"
      >
        {{ task.title }}
      </span>
      <button @click="deleteTask(task)">Delete</button>
    </li>
  </ul>
  <input type="text" v-model="new_task" @keypress.enter="addTask" />
  <button @click="addTask">Add</button>

  <div>
    <p><strong>Completed</strong>:{{ completedTodosCount }}</p>
    <p><strong>Pending</strong>:{{ pendingTodosCount }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      new_task: "",
      todos: [
        { title: "Task 1", completed: true },
        { title: "Task 2", completed: false },
      ],
    };
  },

  computed: {
    completedTodosCount() {
      return this.todos.filter((task) => task.completed === true).length;
    },
    pendingTodosCount() {
      return this.todos.filter((task) => !task.completed).length;
    },
  },

  methods: {
    addTask() {
      if (this.new_task) {
        this.todos.push({ title: this.new_task, completed: false });
        this.new_task = "";
      }
    },

    deleteTask(task) {
      var index = this.todos.indexOf(task);
      this.todos.splice(index, 1);
    },

    toggleTaskStatus(task) {
      task.completed = !task.completed;
    },
  },
};
</script>

<style scoped>
.todos {
  width: 250px;
  padding: 0;
}
.todos li {
  padding: 5px;
}
.todos li button {
  float: right;
}
.completed {
  text-decoration: line-through;
}
</style>