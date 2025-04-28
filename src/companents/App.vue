<template>
  <Header
    v-model:searchQuery="searchQuery"
    :cartItemCount="cart.length"
  />

  <router-view
    v-model:cart="cart"
    :searchQuery="searchQuery"
    :addToCart="addToCart"
  />
</template>

<script setup>
import { ref } from 'vue'
import Header from '@/companents/header.vue' // components yozilishi kerak edi, not companents

// Reactive states
const searchQuery = ref('')
const cart = ref([])

// Item savatchaga qo‘shish funksiyasi
function addToCart(item) {
  const foundItem = cart.value.find(cartItem => cartItem.nomi === item.nomi)
  if (foundItem) {
    foundItem.miqdor += 1
  } else {
    cart.value.push({ ...item, miqdor: 1 })
  }
}
</script>

<style scoped>
/* Agar kerak bo'lsa, umumiy sahifa stylingini shu yerga qo‘shishingiz mumkin */
</style>
