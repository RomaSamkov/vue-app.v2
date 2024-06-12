<template>
  <div>
    <div v-if="!loading" class="content"></div>
    <Loader v-else />
  </div>
</template>

<script>
import { defineComponent } from "vue";
import Loader from "./Loader";
import { useProductStore } from "@/store";

export default defineComponent({
  name: "ProductList",
  components: { Loader },
  setup() {
    const productStore = useProductStore();
    return {};
  },
});
</script>

<style scoped></style>
