<template>
  <div class="child-container">
    <h2><slot name="title"></slot></h2>
    <div><slot name="content"></slot></div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
};
</script>

<style></style>
