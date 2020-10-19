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
import { computed, reactive, toRefs } from "vue";

export default {
  props: {
    title: String,
  },

  setup() {
    const state = reactive({
      new_task: "",
      todos: [
        { title: "Task 1", completed: true },
        { title: "Task 2", completed: false },
      ],
      completedTodosCount: computed(() => {
        return state.todos.filter((task) => task.completed === true).length;
      }),
      pendingTodosCount: computed(() => {
        return state.todos.filter((task) => !task.completed).length;
      }),
    });

    function addTask() {
      if (state.new_task) {
        state.todos.push({ title: state.new_task, completed: false });
        state.new_task = "";
      }
    }

    function deleteTask(task) {
      var index = state.todos.indexOf(task);
      state.todos.splice(index, 1);
    }

    function toggleTaskStatus(task) {
      task.completed = !task.completed;
    }

    return {
      ...toRefs(state),
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