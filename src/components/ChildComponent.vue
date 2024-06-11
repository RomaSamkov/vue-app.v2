<template>
  <div class="child-container">
    <h2><slot name="title"></slot></h2>
    <div><slot></slot></div>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "ChildComponent",
  components: {},
  setup() {
    return {};
  },
});
</script>

<style></style>
