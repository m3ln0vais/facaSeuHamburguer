<template>
  <div>
    <navbar />
    <router-view />
  </div>
</template>

<script>
import navbar from "./components/Navbar.vue";
import Footer from "./components/Footer";

export default {
  components: {
    navbar,
    Footer,
  },
};
</script>
