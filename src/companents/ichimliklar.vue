<template>
  <div class="container">
    <h1 class="title">Ichimliklar</h1>
    <div class="grid">
      <div
        class="item"
        v-for="(drink, index) in filteredIchimliklar"
        :key="index"
      >
        <img :src="drink.rasm" :alt="drink.nomi" class="img" />
        <h2 class="name">{{ drink.nomi }}</h2>
        <p class="price">Narxi: {{ drink.narx }} so'm</p>
        <button class="btn" @click="addToCart(drink)">
          Savatchaga qo‘shish 🛒
        </button>
      </div>
    </div>
    <h2 class="men">Project manager: Qudrat Iskandarov 💻</h2>
  </div>
</template>

<script setup>
import { computed } from 'vue'

// Props
const props = defineProps({
  searchQuery: String,
  addToCart: Function
})

// Rasm importlari
import r1 from '@/assets/co.jpg'
import r2 from '@/assets/fanta1.jpg'
import r3 from '@/assets/pe.jpg'
import r4 from '@/assets/mo.jpeg'
import r5 from '@/assets/choy.jpg'
import r6 from '@/assets/mev.png'
import r7 from '@/assets/0,5l.jpeg'
import r8 from '@/assets/1l.jpg'

import r10 from '@/assets/caco.png'
import r11 from '@/assets/fata.jfif'
import r12 from '@/assets/pepe.jfif'
import r13 from '@/assets/arkb.jpg'
import r14 from '@/assets/fuse.jpg'
import r15 from '@/assets/shisha.jpg'
import r16 from '@/assets/chaynik.png'
import r17 from '@/assets/chashka.jfif'
import r18 from '@/assets/malakam.jpg'
import r19 from '@/assets/qay2.jpg'
import r20 from '@/assets/coppu.jpg'
import r21 from '@/assets/qorac.jpg'

// Ichimliklar ro'yxati
const ichimliklar = [
  { nomi: 'Coca‑Cola 1,5l', narx: '14000', rasm: r1 },
  { nomi: 'Fanta 1,5l', narx: '14000', rasm: r2 },
  { nomi: 'Pepsi 1,5l', narx: '14000', rasm: r3 },
  { nomi: 'Moxito katta grafin', narx: '30000', rasm: r4 },
  { nomi: 'Limon choy', narx: '15000', rasm: r5 },
  { nomi: 'Mevali choy', narx: '30000', rasm: r6 },
  { nomi: 'Suv (0.5L)', narx: '2000', rasm: r7 },
  { nomi: 'Suv (1.5L)', narx: '4000', rasm: r8 },
  
  { nomi: 'Coca‑Cola 1l', narx: '10000', rasm: r10 },
  { nomi: 'Fanta 1l', narx: '10000', rasm: r11 },
  { nomi: 'Pepsi 1l', narx: '10000', rasm: r12 },
  { nomi: 'Ark tea', narx: '10000', rasm: r13 },
  { nomi: 'Fuse tea', narx: '10000', rasm: r14 },
  { nomi: 'Cola shisha', narx: '5000', rasm: r15 },
  { nomi: 'Choy chaynik', narx: '7000', rasm: r16 },
  { nomi: 'Choy chashka', narx: '3000', rasm: r17 },
  { nomi: 'Kofe malakam', narx: '6000', rasm: r18 },
  { nomi: 'Coppuccino', narx: '6000', rasm: r20 },
  { nomi: 'Qaynoq shkaland', narx: '6000', rasm: r19 },
  { nomi: 'Qora kofe', narx: '5000', rasm: r21 },
]

// Filter qilingan ichimliklar (search orqali)
const filteredIchimliklar = computed(() => {
  if (!props.searchQuery) return ichimliklar
  return ichimliklar.filter(drink =>
    drink.nomi.toLowerCase().includes(props.searchQuery.toLowerCase())
  )
})
</script>

<style scoped>
.container {
  padding: 20px;
  text-align: center;
}

.men {
  text-align: center;
  font-family: sans-serif;
  font-size: 18px;
  margin-top: 30px;
  color: #555;
}

.title {
  font-size: 2rem;
  margin-bottom: 20px;
  font-weight: bold;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 20px;
}

.item {
  background: white;
  padding: 15px;
  border-radius: 16px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-radius: 12px;
}

.name {
  margin: 10px 0 5px;
  font-size: 1.2rem;
  font-weight: bold;
}

.price {
  color: #666;
  margin-bottom: 10px;
  font-size: 16px;
}

.btn {
  background-color: #0ea5e9;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
  transition: background-color 0.3s;
}

.btn:hover {
  background-color: #0284c7;
}
</style>
