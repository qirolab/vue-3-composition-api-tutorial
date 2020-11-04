<template>
  <div style="border: 1px solid">
    <h1>Teleport Example</h1>
    <teleport to="#destination" :disabled="disableTeleport">
      <p>It should be outside TeleportExample component.</p>
    </teleport>
    <teleport to="#destination">
      <p>Teleport text 2</p>
    </teleport>
    <button @click="disableTeleport = !disableTeleport">Toggle Teleport</button>

    <teleport to="#destination">
      <VModal ref="modal">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dolor itaque
        totam esse eius quia? Temporibus odit optio consequuntur. Debitis ut
        nesciunt accusamus quasi. Adipisci voluptate pariatur nam deleniti, quas
        similique!
      </VModal>
    </teleport>
    <button @click="showModal">Show Modal</button>
  </div>
</template>

<script>
import VModal from "./VModal";
import { ref } from "vue";

export default {
  components: {
    VModal,
  },

  setup() {
    const disableTeleport = ref(false);

    const modal = ref(null);

    function showModal() {
      modal.value.show();
    }

    return {
      disableTeleport,
      modal,
      showModal,
    };
  },
};
</script>

<style>
</style>