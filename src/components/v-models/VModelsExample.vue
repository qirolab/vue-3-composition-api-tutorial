<template>
  <h2>v-model</h2>
  <VEditor v-model:content="content" v-model:title="title" />

  <h2>{{ title }}</h2>
  {{ content }}
</template>

<script>
import { ref } from "vue";
import VEditor from "./VEditor";

export default {
  components: {
    VEditor,
  },

  setup() {
    const title = ref("");
    const content = ref("");

    return {
      title,
      content,
    };
  },
};
</script>