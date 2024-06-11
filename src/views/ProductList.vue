<template>
  <div>
    <h1>Products</h1>
    <div v-if="loading"><p>...Loading</p></div>
    <div v-else>
      <ul class="products-list">
        <template v-for="product in products" :key="product.id">
          <router-link :to="`/products/${product.id}`"
            ><li>{{ product.title }}</li>
          </router-link>
        </template>
      </ul>
    </div>
  </div>
</template>

<script>
import { defineComponent, onMounted, ref } from "vue";
import axios from "axios";

export default defineComponent({
  name: "ProductList",
  components: {},
  setup() {
    const products = ref({});
    const loading = ref(true);

    onMounted(async () => {
      const response = await axios.get("https://fakestoreapi.com/products");
      products.value = response.data;
      loading.value = false;
    });
    return { products, loading };
  },
});
</script>

<style scoped>
.products-list {
  display: grid;
  grid-template-columns: repeat(3, auto);
  gap: 2px;
}

.products-list li {
  display: grid;
  justify-content: center;
  justify-items: center;
  align-items: center;
  text-align: center;
  height: 100px;
  border: 1px solid pink;
  border-radius: 5px;
  padding: 20px;
}

.products-list li:hover {
  border: 1px solid #fff;
  color: #fff;
  background: #acafbe;
}

a:hover {
  text-decoration: none;
}
</style>
