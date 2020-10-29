<template>
  <h2>Watchers in Vue 3</h2>
  <div>
    Name:
    <input type="text" v-model="name" />
    <p>name: {{ name }}</p>
  </div>
  <div>
    Email:
    <input type="text" v-model="email" />
    <p>Email: {{ email }}</p>
  </div>
</template>

<script>
import { ref, watch } from "vue";
export default {
  setup() {
    const name = ref("");
    const email = ref("");

    // let stopWatchEffect = watchEffect(() => {
    //   console.log("watchEffect name", name.value.length);
    //   console.log("watchEffect email", email.value);

    //   if (name.value.length === 10) {
    //     stopWatchEffect();
    //   }
    // });

    let stopWatch = watch(
      [name, email],
      ([newName, newEmail], [prevName, prevEmail]) => {
        console.log("newName:", newName.length);
        console.log("newEmail:", newEmail);
        console.log("prevName:", prevName);
        console.log("prevEmail:", prevEmail);

        if (name.value.length === 5) {
          stopWatch();
        }
      },
      { immediate: true }
    );

    return {
      name,
      email,
    };
  },
};
</script>

<style>
</style>