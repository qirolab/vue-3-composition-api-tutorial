<template>
  <h2>Editor</h2>
  <div>
    Title:<br />
    <input type="text" :value="title" @input="updateTitle" />
  </div>
  <div style="margin-top: 15px">
    Content:<br />
    <input type="text" :value="content" @input="updateValue" />
  </div>
</template>

<script>
export default {
  props: {
    content: String,
    title: String,
  },

  setup(props, context) {
    function updateTitle(event) {
      context.emit("update:title", event.target.value);
    }

    function updateValue(event) {
      context.emit("update:content", event.target.value);
    }

    return {
      updateTitle,
      updateValue,
    };
  },
};
</script>

<style>
</style>