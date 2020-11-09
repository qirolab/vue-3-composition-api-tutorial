<template>
  <h1>Suspense Example</h1>

  <div v-if="errMsg">{{ errMsg }}</div>
  <Suspense v-else>
    <template #default>
      <Users />
    </template>
    <template #fallback>
      <div>Loading ...</div>
    </template>
  </Suspense>
</template>

<script>
import { onErrorCaptured, ref } from "vue";
import Users from "./Users";

export default {
  components: {
    Users,
  },

  setup() {
    const errMsg = ref(null);

    onErrorCaptured(() => {
      errMsg.value = "Something went wrong";
    });

    return {
      errMsg,
    };
  },
};
</script>