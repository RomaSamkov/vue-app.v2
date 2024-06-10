<template>
  <div class="main-block">
    <button @click="showModal">Show Modal</button>
    <br /><br /><br />
    <label for="modalTitle">Title</label>
    <input type="text" id="modalTitle" v-model="modalTitle" />
    <label for="modalMessage">Message</label>
    <input type="text" id="modalMessage" v-model="modalMessage" />
    <Modal
      v-if="isModealOpen"
      :modal-title="modalTitle"
      :modal-message="modalMessage"
      @close="closeModal"
    />
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";
import Modal from "./components/Modal.vue";

export default defineComponent({
  name: "App",
  components: { Modal },
  setup() {
    const isModealOpen = ref(false);
    const modalTitle = ref("");
    const modalMessage = ref("");

    function showModal() {
      isModealOpen.value = true;
      modalTitle.value = "Default Title";
      modalMessage.value = "Default Message";
    }

    function closeModal() {
      isModealOpen.value = false;
      modalTitle.value = "";
      modalMessage.value = "";
    }
    return {
      isModealOpen,
      modalTitle,
      modalMessage,
      showModal,
      closeModal,
    };
  },
});
</script>

<style>
.price-block {
  text-align: center;
}
</style>
