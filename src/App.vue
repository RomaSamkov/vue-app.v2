<template>
  <div v-if="!loading" class="content"></div>
  <Loader v-else />
</template>

<script>
import { computed, defineComponent, onMounted, ref } from "vue";

import Loader from "./components/Loader.vue";
import { fetchAllPhotos } from "./api/fetchData";

export default defineComponent({
  name: "App",
  components: { Loader },
  setup() {
    const currentPage = ref(1);
    const perPage = ref(15);
    const photosCount = ref(0);
    const loading = ref(true);

    const handleChangePage = (page) => {
      currentPage.value = page;
    };

    const pageCount = computed(() => {
      return Math.ceil(photosCount.value / perPage.value);
    });

    onMounted(() => {
      fetchAllPhotos()
        .then((data) => {
          photosCount.value = data.length;
          loading.value = false;
        })
        .catch((error) => {
          console.log(error);
          loading.value = false;
        });
    });

    return {
      currentPage,
      perPage,
      photosCount,
      loading,
      handleChangePage,
      pageCount,
    };
  },
});
</script>

<style>
* {
  font-family: "Lexend", sans-serif;
}

ul {
  list-style: none;
  padding: 0;
}

button {
  cursor: pointer;
  border: 1px solid rgba(0, 0, 0, 0.3);
  padding: 5px 10px;
  font-style: normal;
  font-weight: 600;
  font-size: 19px;
  text-align: center;
  color: #fff;
  background: #79c56e;
  border-radius: 6px;
}
</style>
