<template>
  <div class="parent-container">
    <h2>Parent Component</h2>
    <ChildComponent>
      <template v-slot:title>Child Component Title</template>
      <p>
        Child Component Content Lorem ipsum dolor sit amet consectetur,
        adipisicing elit. Nisi molestias voluptatum, reprehenderit minus,
        corporis quae eaque, nemo porro rerum repellat sed minima totam itaque
        dolore magni numquam laudantium soluta beatae.
      </p>
    </ChildComponent>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import ChildComponent from "./ChildComponent.vue";

export default defineComponent({
  name: "ParentComponent",
  components: { ChildComponent },
  setup() {
    return {};
  },
});
</script>

<style></style>
