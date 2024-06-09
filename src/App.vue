<template>
  <div class="main-block"><button @click="showModal">Show Modal</button></div>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "App",
  setup() {
    const isModealOpen = ref(false);
    const modalTitle = ref("");
    const modalMessage = ref("");
    return {
      isModealOpen,
      modalTitle,
      modalMessage,
    };
  },
});
</script>

<style>
.price-block {
  text-align: center;
}
</style>
