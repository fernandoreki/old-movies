<script setup>
import Movies from './components/Movies.vue';
import Header from './components/Header.vue';

</script>

<template>
  <div class="bg-dark">
    <Header />
    <div class="container">
      <h1 class="mt-3 mb-3 text-light">Old movies database</h1>
    </div>
    <Movies />
  </div>
</template>
<style scoped>
</style>
