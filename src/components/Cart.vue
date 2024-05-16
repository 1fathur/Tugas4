<template>
    <div class="my-4">
      <h2>Keranjang Belanja</h2>
      <ul class="list-group">
        <CartItem v-for="item in cartItems" :key="item.id" :item="item" />
      </ul>
      <p v-if="cartItems.length === 0" class="mt-3">Keranjang Anda kosong</p>
      <p class="mt-3"><strong>Total:</strong> Rp {{ formatPrice(total) }}</p>
      <button class="btn btn-success mt-3" @click="checkout">Checkout</button>
    </div>
  </template>
  
  <script setup>
  import { defineProps, computed } from 'vue';
  import Swal from 'sweetalert2';
  import 'sweetalert2/dist/sweetalert2.min.css';
  import CartItem from './CartItem.vue';
  
  const props = defineProps({
    cartItems: {
      type: Array,
      required: true
    }
  });
  
  const total = computed(() => {
    return props.cartItems.reduce((sum, item) => sum + item.price, 0);
  });
  
  const formatPrice = (value) => {
    return value.toLocaleString('id-ID');
  };
  
  const checkout = async () => {
    const { value: paymentMethod } = await Swal.fire({
      title: 'Pilih metode pembayaran',
      input: 'radio',
      inputOptions: {
        cash: 'Tunai',
        debit: 'Debit'
      },
      inputValidator: (value) => {
        if (!value) {
          return 'Anda harus memilih salah satu!'
        }
      }
    });
  
    if (paymentMethod) {
      if (paymentMethod === 'cash') {
        Swal.fire('Pembayaran berhasil!', '', 'success');
        resetCart();
      } else if (paymentMethod === 'debit') {
        const { value: cardNumber } = await Swal.fire({
          title: 'Masukkan nomor kartu debit Anda',
          input: 'text',
          inputPlaceholder: 'Masukkan nomor kartu',
          inputValidator: (value) => {
            if (!value) {
              return 'Anda harus memasukkan nomor kartu!'
            }
          }
        });
  
        if (cardNumber) {
          Swal.fire('Pembayaran berhasil!', '', 'success');
          resetCart();
        }
      }
    }
  };
  
  const resetCart = () => {
    props.cartItems.splice(0);
  };
  </script>
  
  