<template>
  <v-app>
    <v-main class="body d-flex justify-center align-center">
      <HomePage />
    </v-main>
  </v-app>
</template>

<script>
import HomePage from "./components/HomePage.vue";
</script>
<style scoped>
.body {
  background-color: hsl(228, 11%, 9%);
}
</style>