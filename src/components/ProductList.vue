<template>
  <div>
    <div v-if="!loading" class="content"></div>
    <Loader v-else />
  </div>
</template>

<script>
import { defineComponent, onMounted } from "vue";
import Loader from "./Loader";
import { useProductStore } from "@/store";

export default defineComponent({
  name: "ProductList",
  components: { Loader },
  setup() {
    const productStore = useProductStore();
    onMounted(() => {
      fetchProducts();
    });

    const fetchProducts = () => {
      productStore.fetchProducts();
    };

    const addProduct(product) = () => {
      productStore.addProduct(product)
    }



    return {};
  },
});
</script>

<style scoped></style>
