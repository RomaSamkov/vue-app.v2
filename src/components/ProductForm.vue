<template>
  <form @submit.prevent="handleSubmit">
    <p>Create Product</p>
    <div class="inputs-container">
      <div class="title-block">
        <label for="title">Title:</label
        ><input type="text" name="" id="title" v-model="title" />
      </div>
      <div class="price-block">
        <label for="price">Price:</label
        ><input type="number" name="" id="price" v-model="price" />
      </div>
    </div>
    <button type="submit">Add Product</button>
  </form>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "ProductForm",
  components: {},
  emits: ["product-added"],
  setup(_, { emit }) {
    const title = ref("");
    const price = ref("");

    const handleSubmit = () => {
      emit("product-added", {
        title: title.value,
        price: Number(price.value),
        id: "@",
      });
      title.value = "";
      price.value = "";
    };
    return { title, price, handleSubmit };
  },
});
</script>

<style scoped>
form {
  padding: 20px;
  border: 1px solid #000;
  border-radius: 15px;
}

.inputs-container {
  display: grid;
  gap: 10px;
  padding-bottom: 20px;
}

.title-block,
.price-block {
  display: grid;
  grid-template-columns: repeat(2, auto);
  justify-content: end;
  gap: 30px;
}
</style>
