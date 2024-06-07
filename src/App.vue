<template>
  <div>
    <h2>Hello, {{ name }}</h2>
    <div class="container">
      <button v-on:click="flag = !flag">Click</button>
      <h2 v-if="flag">Hello!</h2>
      <h2 v-else>Bye Bye!</h2>
    </div>
    <div class="container-2">
      <button @click="count = count + 1">Click + 1</button>
      <p>{{ count }}</p>
    </div>
    <div class="container-3">
      <input type="text" v-model="text" />
      <p>{{ text }}</p>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "App",
  components: {},
  setup() {
    const name = "Roma RS";
    const flag = ref(true);
    const count = ref(0);
    const text = ref("");
    return { name, flag, count, text };
  },
});
</script>

<style>
h2 {
  text-align: center;
}
</style>
