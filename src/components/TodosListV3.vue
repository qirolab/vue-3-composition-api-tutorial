<template>
  <h2>{{ title }}</h2>
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
import { computed, ref } from "vue";

export default {
  props: {
    title: String,
  },

  setup() {
    const new_task = ref("");

    const todos = ref([
      { title: "Task 1", completed: true },
      { title: "Task 2", completed: false },
    ]);

    const completedTodosCount = computed(() => {
      return todos.value.filter((task) => task.completed === true).length;
    });

    const pendingTodosCount = computed(() => {
      return todos.value.filter((task) => !task.completed).length;
    });

    function addTask() {
      if (new_task.value) {
        todos.value.push({ title: new_task.value, completed: false });
        new_task.value = "";
      }
    }

    function deleteTask(task) {
      var index = todos.value.indexOf(task);
      todos.value.splice(index, 1);
    }

    function toggleTaskStatus(task) {
      task.completed = !task.completed;
    }

    return {
      new_task,
      todos,
      completedTodosCount,
      pendingTodosCount,
      addTask,
      deleteTask,
      toggleTaskStatus,
    };
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