<template>
  <Cards />
</template>

<script>
import { defineComponent } from "vue";
import Cards from "./components/Cards.vue";

export default defineComponent({
  name: "App",
  components: { Cards },
});
</script>

<style>
h2 {
  text-align: center;
}
</style>
