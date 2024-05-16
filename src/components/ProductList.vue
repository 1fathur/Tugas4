<template>
    <div class="container">
      <h1 class="my-4">Daftar Produk</h1>
      <div class="row">
        <ProductItem 
          v-for="product in products" 
          :key="product.id" 
          :product="product" 
          @add-to-cart="addToCart" 
          class="col-md-4 mb-4" 
        />
      </div>
      <Cart :cartItems="cartItems" @checkout="checkout" />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import ProductItem from './ProductItem.vue';
  import Cart from './Cart.vue';
  
  const products = ref([
    { id: 1, name: 'Apel Fuji', price: 15000, image: 'https://sesa.id/cdn/shop/products/sssgid.zone-1690190707-Apel-Fuji-Blush-950---1000-gr-_2_-removebg-preview.png?v=1690190871' },
    { id: 2, name: 'Pisang Cavendish', price: 12000, image: 'https://sesa.id/cdn/shop/products/sssgid.zone-1707725915-SKU_-_2024-02-12T151816.833.jpg?v=1707725949' },
    { id: 3, name: 'Jeruk Sunkist', price: 18000, image: 'https://down-id.img.susercontent.com/file/id-11134207-7r98v-lm43ps4kb25w99' },
    { id: 4, name: 'Mangga Harum Manis', price: 25000, image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRtPYmtqbGuEtYg0s5VwDBd6FA_VMaaxU_03EWWKrlnBg&s' },
    { id: 5, name: 'Anggur Merah', price: 90000, image: 'https://www.canggusky.com/wp-content/uploads/2022/09/anggurmerah.jpg' },
    { id: 6, name: 'Semangka Tanpa Biji', price: 20000, image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRBTuXpr8NcWLO0NeSYz85F0zJax2l93TnPBmG_X8wGhQ&s' },
  ]);
  
  const cartItems = ref([]);
  
  const addToCart = (product) => {
    cartItems.value.push(product);
  };
  
  const checkout = () => {
  };
  </script>

  
  