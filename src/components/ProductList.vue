<template>
  <div>
    <div v-if="!productStore.loading" class="content">
      <div class="panel">
        <ProductForm @product-added="addProduct" />
        <button @click="sortProduct">Sort by Price</button>
      </div>
      <ul class="product-list">
        <li v-for="product in productStore.products" :key="product.id">
          {{ product.title }} - {{ product.price }}
          <div class="number">{{ product.id }}</div>
          <button @click="removeProduct(product.id)">Remove</button>
        </li>
      </ul>
    </div>
    <Loader v-else />
  </div>
</template>

<script>
import { defineComponent, onMounted } from "vue";
import Loader from "./Loader";
import { useProductStore } from "@/store";
import ProductForm from "./ProductForm.vue";

export default defineComponent({
  name: "ProductList",
  components: { Loader, ProductForm },
  setup() {
    const productStore = useProductStore();
    onMounted(() => {
      fetchProducts();
    });

    const fetchProducts = () => {
      productStore.fetchProducts();
    };

    const addProduct = (product) => {
      productStore.addProduct(product);
    };

    const removeProduct = (productId) => {
      productStore.removeProduct(productId);
    };

    const sortProduct = () => {
      productStore.sortProducts();
    };

    return {
      productStore,
      addProduct,
      removeProduct,
      sortProduct,
    };
  },
});
</script>

<style scoped>
.panel {
  display: grid;
  grid-template-columns: repeat(2, auto);
  gap: 40px;
  align-items: center;
  justify-items: center;
  justify-content: center;
}

.product-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.product-list li {
  position: relative;
  display: grid;
  align-items: center;
  justify-items: center;
  justify-content: center;
  text-align: center;
  height: 100px;
  padding: 20px;
  border: 1px solid #000;
  border-radius: 15px;
  background: #c6dcc3;
}

.number {
  position: absolute;
  top: 0;
  left: 0;
  padding: 15px;
}
</style>
