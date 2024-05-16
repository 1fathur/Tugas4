<template>
    <div class="card">
      <img :src="product.image" class="card-img-top img-thumbnail small-img" :alt="product.name">
      <div class="card-body">
        <h5 class="card-title">{{ product.name }}</h5>
        <p class="card-text">Rp {{ formatPrice(product.price) }}</p>
        <button class="btn btn-primary" @click="addToCart">Tambah ke Keranjang</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    product: Object
  });
  
  const emit = defineEmits(['add-to-cart']);
  
  const addToCart = () => {
    emit('add-to-cart', props.product);
  };
  
  const formatPrice = (value) => {
    return value.toLocaleString('id-ID');
  };
  </script>
  
  <style scoped>
  .card {
    width: 49.5%;
    height: min-content;
    margin-left: 3px;
    background-color: transparent;
  }
  
  .small-img {
    width: 100px;
    height: 100px; 
    object-fit: cover; 
  }
  </style>
  