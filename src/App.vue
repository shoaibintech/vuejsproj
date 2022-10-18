
<template>
  <Header title="contact" />

  <RouterView />
  <Footer />
</template>
  
<script >
import Header from "./components/Header.vue";
import { RouterLink, RouterView } from "vue-router";
import Footer from "./components/Footer.vue";
export default {
  name: "App",
  components: {
    Header,
    Footer,
    RouterView,
  },
};
</script>


