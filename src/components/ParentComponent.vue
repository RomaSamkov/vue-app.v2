<template>
  <div class="parent-container">
    <h2>Parent Component</h2>
    <ChildComponent>
      <template v-slot:title>Child Component Title</template>
      <template v-slot:content
        >Child Component Content Lorem ipsum dolor sit amet consectetur,
        adipisicing elit. Nisi molestias voluptatum, reprehenderit minus,
        corporis quae eaque, nemo porro rerum repellat sed minima totam itaque
        dolore magni numquam laudantium soluta beatae.</template
      >
    </ChildComponent>
  </div>
</template>

<script>
import ChildComponent from "./ChildComponent.vue";

export default {
  name: "App",
  components: { ChildComponent },
};
</script>

<style></style>
