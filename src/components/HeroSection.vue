<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const currentSlide = ref(0)
let intervalId = null
const images = [
  'https://comex-assets.s3.amazonaws.com/comex-assets/web/posts/6737/transformacion-digital-260321-095759.png',
  
  'https://d5tnfl9agh5vb.cloudfront.net/uploads/2024/08/transformacion-digital.jpg',
  
  'https://rosanarosas.com/wp-content/uploads/2017/11/transformacion-digital.png'
]

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % images.length
}

// Iniciar el carrusel 
onMounted(() => {
  intervalId = setInterval(nextSlide, 3500) 
})

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId)
})
</script>

<template>
  <section class="bg-white pt-20 pb-24 overflow-hidden font-sans">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center relative z-10">
      <h1 class="text-5xl md:text-6xl font-extrabold text-[#06b6d4] leading-tight mb-6 tracking-tight">
        Transformación Digital en SST, <br class="hidden md:block" />
        Gestión Humana y Proveedores
      </h1>
      <p class="mt-6 max-w-2xl mx-auto text-xl text-gray-500 mb-10 leading-relaxed">
        Plataforma de Gestión de Recursos Humanos Simplificada. Centraliza tu gestión con control de ausencias, legajos y vacaciones.
      </p>
      <div class="flex justify-center gap-4 mb-16">
        <button class="bg-[#06b6d4] text-white px-8 py-4 rounded-full font-bold shadow-lg hover:bg-cyan-500 transition-transform hover:scale-105 text-lg">
          Más información
        </button>
      </div>

      <div class="relative mx-auto max-w-5xl">
        <div class="bg-gray-900 border-8 border-gray-100 rounded-3xl shadow-2xl overflow-hidden aspect-video relative group">
            <div v-for="(img, index) in images" :key="index"
                 class="absolute inset-0 w-full h-full transition-opacity duration-1000 ease-in-out"
                 :class="currentSlide === index ? 'opacity-100' : 'opacity-0'">
                <img :src="img" alt="Dashboard Screen" class="w-full h-full object-cover" />
                <div class="absolute inset-0 bg-black/10"></div>
            </div>

            <div class="absolute bottom-4 left-0 right-0 flex justify-center gap-2 z-10">
                <button 
                    v-for="(img, index) in images" 
                    :key="index"
                    @click="currentSlide = index"
                    class="w-3 h-3 rounded-full transition-all duration-300 shadow-sm"
                    :class="currentSlide === index ? 'bg-white scale-125' : 'bg-white/50 hover:bg-white/80'">
                </button>
            </div>
        </div>
        <div class="absolute -inset-4 bg-gradient-to-r from-cyan-500 to-blue-500 rounded-[2.5rem] blur-2xl opacity-20 -z-10"></div>
      </div>
    </div>
  </section>
</template>