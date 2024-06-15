<template>
  <div v-if="loading" class="content">
    <h1 class="text">Gallery</h1>
    <div class="gallery">
      <div class="photo" v-for="photo in photos" :key="photo.id">
        <img :src="photo.thumbnailUrl" :alt="photo.title" />
        <p>{{ photo.title }}</p>
      </div>
    </div>
  </div>
  <Loader v-else />
</template>

<script>
import { defineComponent, ref, watchEffect } from "vue";
import Loader from "./Loader";
import { fetchPhotos } from "@/api/fetchData";

export default defineComponent({
  name: "ProductList",
  components: { Loader },
  props: {
    page: {
      type: Number,
      required: true,
    },
    limit: {
      type: Number,
      required: true,
    },
  },
  setup(props) {
    const photos = ref([]);
    const loading = ref(true);

    const loadPhotos = async () => {
      photos.value = await fetchPhotos(props.page, props.limit);
    };

    watchEffect(() => {
      loadPhotos();
    });

    return { photos, loading, loadPhotos };
  },
});
</script>

<style scoped>
.gallery {
  display: grid;
  grid-template-columns: repeat(5, 200px);
  gap: 40px, 20px;
  align-items: start;
  justify-content: center;
  padding: 0 20px 20px 20px;
}

.product-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.photo {
  display: grid;
  align-items: center;
  justify-items: center;
  justify-content: center;
  text-align: center;
  height: 205px;
  overflow-y: scroll;
}

.photo p {
  max-width: 140px;
}

.text {
  text-align: center;
}
</style>
