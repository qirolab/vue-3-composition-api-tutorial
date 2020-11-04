<template>
  <div class="modal" v-show="isOpen">
    <span class="close" @click="hide">&times;</span>
    <div class="modal-content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const isOpen = ref(false);

    function hide() {
      isOpen.value = false;
    }

    function show() {
      isOpen.value = true;
    }

    return {
      isOpen,
      hide,
      show,
    };
  },
};
</script>

<style>
.modal {
  position: absolute;
  z-index: 999;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
}
.modal-content {
  background-color: #ffffff;
  margin: 15% auto;
  padding: 20px;
  width: 500px;
  border: 1px solid #888;
}
.close {
  padding: 10px;
  cursor: pointer;
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}
</style>