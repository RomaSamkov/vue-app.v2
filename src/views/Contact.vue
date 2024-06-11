<template>
  <div>
    <h1>Contact US!</h1>
    <p>Hello User!</p>
    <div v-if="loading"><p>...Loading</p></div>
    <div v-else>
      <p><strong>Email: </strong>{{ contactInfo?.email }}</p>
      <p><strong>Phone: </strong>{{ contactInfo?.phone }}</p>
      <p><strong>City: </strong>{{ contactInfo?.address?.city }}</p>
      <p><strong>Street: </strong>{{ contactInfo?.address?.street }}</p>
      <p><strong>Code: </strong>{{ contactInfo?.address?.zipcode }}</p>
    </div>
  </div>
</template>

<script>
import { defineComponent, onMounted, ref } from "vue";
import axios from "axios";

export default defineComponent({
  name: "Contact",
  components: {},
  setup() {
    const loading = ref(true);
    const contactInfo = ref({});

    onMounted(async () => {
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/users/1"
        );
        contactInfo.value = response.data;
        loading.value = false;
      } catch (error) {
        console.log(error);
        loading.value = false;
      }
    });
    return { loading, contactInfo };
  },
});
</script>

<style></style>
