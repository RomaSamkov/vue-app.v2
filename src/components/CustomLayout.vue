<template>
  <div class="custom-layout"><slot></slot></div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "CustomLayout",
  components: {},
  setup() {
    return {};
  },
});
</script>

<style scoped>
.custom-layout {
  padding: 20px;
  margin: 0 auto;
  max-width: 1200px;
}
</style>
