<template>
  <h2>Users</h2>

  <User v-for="user in users" :key="user.id" :user="user" />
</template>

<script>
import axios from "axios";
import { defineAsyncComponent, ref } from "vue";

// import User from "./User";
const User = defineAsyncComponent(() =>
  import("./User" /* webpackChunkName:"user" */)
);

export default {
  components: {
    User,
  },

  async setup() {
    const users = ref(null);

    const response = await axios.get(
      "https://jsonplaceholder.typicode.com/users"
    );

    users.value = response.data;

    return {
      users,
    };
  },
};
</script>

<style>
</style>