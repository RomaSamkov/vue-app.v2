<template>
  <Header />
  <CustomLayout>
    <router-view></router-view>
  </CustomLayout>
</template>

<script>
import { defineComponent } from "vue";
import Header from "./components/Header.vue";
import CustomLayout from "./components/CustomLayout.vue";

export default defineComponent({
  name: "App",
  components: { Header, CustomLayout },
  setup() {
    return {};
  },
});
</script>

<style>
ul {
  list-style: none;
  padding: 0;
}
a {
  text-decoration: none;
  color: black;
}
a:hover {
  text-decoration: underline;
}
</style>
