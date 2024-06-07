<template>
  <ul class="card" v-for="card in arrayCard" :key="card.name">
    <img :src="card.src" :alt="card.alt" style="width: 100px" />
    <li>{{ card.name }} - {{ card.age }}</li>
  </ul>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "Card",
  setup() {
    return {};
  },
  props: {
    arrayCard: Array,
  },
});
</script>

<style scoped></style>
