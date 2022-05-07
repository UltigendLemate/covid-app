<template>
  <Header />

  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/form">Form</router-link>
  </nav>
  <div class="container">
    <router-view />
  </div>
</template>

<script>
import Header from "@/components/Header";

export default {
  components: {
    Header
  },
};
</script>

