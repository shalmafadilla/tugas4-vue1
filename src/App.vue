<script setup>
import { ref } from 'vue'; // Import ref untuk reactive data

// Impor gambar lokal dari folder assets
import image1 from '@/assets/pict1.png';
import image2 from '@/assets/pict2.png';
import image3 from '@/assets/pict3.png';
import image4 from '@/assets/pict4.png';

const count = ref(0); // Inisialisasi counter
const color = ref('lightgray'); // Inisialisasi warna
const currentImageIndex = ref(0); // Inisialisasi index gambar yang tampil saat ini

// Daftar gambar lokal untuk carousel
const images = [image1, image2, image3, image4];

function increment() {
  count.value++; // Fungsi untuk menambah counter
}

function changeColor() {
  // Mengubah warna secara acak
  const colors = ['lightgray', 'lightblue', 'lightgreen', 'lightcoral', 'lightyellow'];
  color.value = colors[Math.floor(Math.random() * colors.length)];
}

function nextImage() {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.length; // Pindah ke gambar berikutnya
}

function prevImage() {
  currentImageIndex.value = (currentImageIndex.value - 1 + images.length) % images.length; // Pindah ke gambar sebelumnya
}
</script>

<template>
  <div>
    <p>Berhitung: {{ count }}</p>
    <button @click="increment">Tambah</button>
    
    <div :style="{ backgroundColor: color, width: '200px', height: '200px', margin: '20px auto', borderRadius: '50%' }"></div>
    <button @click="changeColor">Ubah Warna</button>
    
    <div class="carousel">
      <img :src="images[currentImageIndex]" alt="carousel image" />
      <div class="carousel2">
      <button @click="prevImage">Previous</button>
      <button @click="nextImage">Next</button>
    </div>
    </div>
  </div>
</template>

<style scoped>
div {
  text-align: center;
  margin-top: 2px;
}

button {
  padding: 10px 15px;
  font-size: 17px;
  cursor: pointer;
  border-radius: 10px;
  color: rgb(0, 0, 0);
  margin: 0 50px;
}

button:hover{
  background-color: rgb(255, 149, 248);
}

div > div {
  transition: background-color 0.3s ease;
}

.carousel {
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.carouse2 {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}


.carousel img {
  width: 600px;
  height: 200px;
  object-fit: cover;
  margin: 0 10px;
  border-radius: 10px;
}
</style>