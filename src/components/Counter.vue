<template>
  <h2>Counter (child component) {{ counter }}</h2>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  props: {
    counter: Number,
  },
  setup() {
    return {};
  },
});
</script>

<style>
.price-block {
  text-align: center;
}
</style>
