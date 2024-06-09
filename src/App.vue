<template>
  <input type="number" name="" id="" v-model="counter" />
  <Counter :counter="counter" />
</template>

<script>
import { defineComponent, ref } from "vue";
import Counter from "./components/Counter.vue";

export default defineComponent({
  components: { Counter },
  name: "App",
  setup() {
    const counter = ref(0);
    return { counter };
  },
});
</script>

<style>
.price-block {
  text-align: center;
}
</style>
