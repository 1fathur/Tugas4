<template>
    <li class="list-group-item">
      {{ item.name }} - Rp {{ formatPrice(item.price) }}
    </li>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    item: Object
  });
  
  const formatPrice = (value) => {
    return value.toLocaleString('id-ID');
  };
  </script>
  

  