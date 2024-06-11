<template>
  <div v-if="loading"><p>...Loading</p></div>
  <div v-else>
    <h1>{{ product?.title }}</h1>
    <p>{{ product?.description }}</p>
    <p>Price: {{ product?.price }}$</p>
    <p>Rating: {{ product?.rating?.rate }}/10</p>
    <img class="product-image" :src="product?.image" :alt="`image-${id}`" />
  </div>
</template>

<script>
import { defineComponent, onMounted, ref } from "vue";
import axios from "axios";

export default defineComponent({
  name: "Product",
  props: {
    id: {
      type: String,
      required: true,
    },
  },
  components: {},
  setup(props) {
    const product = ref(null);
    const loading = ref(true);
    onMounted(async () => {
      const response = await axios.get(
        `https://fakestoreapi.com/products/${props.id}`
      );
      product.value = response.data;
      loading.value = false;
    });
    return { product, loading };
  },
});
</script>

<style scoped>
.product-image {
  width: 400px;
}
</style>
