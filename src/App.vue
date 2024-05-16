<template>
  <div class="background">

  </div>
  <div id="app" class="container">
    <ProductList />
  </div>
</template>

<script setup>
import ProductList from './components/ProductList.vue';
</script>

<style scoped>
.background{
  background-image: url('src/assets/image.png');
  position: fixed;
  top: 0;
  left: 0;
  min-height: 90%;
  min-width: 1500px;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: -2;
  object-fit: cover;
  -webkit-background-size:cover; -moz-background-size:cover; -o-background-size:cover; background-size: cover;
  filter: brightness(0.8);
}
</style>
