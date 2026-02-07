<script setup>
import { ref } from 'vue'
import imgRecurso1 from '@/assets/recurso1.png' 
import imgRecurso2 from '@/assets/recurso2.png'
import imgRecurso3 from '@/assets/recurso3.png'
import imgRecurso4 from '@/assets/recurso4.png'

const resources = [
  {
    id: 1,
    title: 'Formatos útiles de SST',
    subtitle: 'Leyes, guías y reglamentos',
    image: imgRecurso1 
  },
  {
    id: 2,
    title: 'Brochure',
    subtitle: 'Nuestros servicios',
    image: imgRecurso2
  },
  {
    id: 3,
    title: 'Información sobre utilidades',
    subtitle: 'Información sobre utilidades',
    image: imgRecurso3
  },
  {
    id: 4,
    title: 'Texto informativo sobre normas ISO',
    subtitle: 'Texto informativo sobre normas ISO',
    image: imgRecurso4
  }
]
</script>

<template>
  <div class="bg-white min-h-screen pb-24 font-sans">
    
    <div class="bg-gradient-to-r from-[#0aafe6] to-[#04619f] text-white overflow-hidden relative">
        <div class="max-w-7xl mx-auto px-6 py-16 md:py-20 flex flex-col md:flex-row items-center justify-between gap-12">
            <div class="md:w-1/2 z-10 text-center md:text-left">
                <h1 class="text-3xl md:text-5xl font-extrabold leading-tight tracking-tight drop-shadow-md">
                    ¡Accede a nuestros Ebooks <br class="hidden md:block"/> y Guías de forma gratuita!
                </h1>
            </div>
            <div class="md:w-1/2 flex justify-center z-10 relative">
                 <div class="absolute inset-0 bg-white/20 blur-3xl rounded-full transform scale-75"></div>
                 <div class="w-full max-w-lg aspect-video relative flex items-center justify-center">
                    <div class="w-full h-48 bg-white/10 backdrop-blur-md border border-white/30 rounded-xl flex items-center justify-center shadow-2xl transform -rotate-2">
                        <img src="https://www.juancmejia.com/wp-content/uploads/2022/05/computadoras-para-transformacion-digital.jpg" alt="Ebook" class="w-full h-full object-cover rounded-lg shadow-lg">
                    </div>
                 </div>
            </div>
        </div>
    </div>

    <div class="text-center pt-16 pb-12">
        <h2 class="text-4xl font-extrabold text-[#0aafe6]">Descargables</h2>
    </div>

    <div class="max-w-5xl mx-auto px-6">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-x-12 gap-y-16">
            
            <div v-for="item in resources" :key="item.id" class="flex flex-col items-center">
                
                <div class="bg-white rounded-[2rem] shadow-lg border border-gray-100 overflow-hidden w-full transition-transform duration-300 hover:-translate-y-2 hover:shadow-xl group cursor-pointer">
                    
                    <div class="h-56 relative overflow-hidden bg-gray-100">
                         <img 
                            :src="item.image" 
                            :alt="item.title"
                            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                         />
                    </div>

                    <div class="p-6 text-center">
                         <h3 class="text-xl font-bold text-[#0aafe6] mb-1 leading-tight">{{ item.title }}</h3>
                         <p class="text-gray-400 text-xs font-bold uppercase tracking-wide">{{ item.subtitle }}</p>
                    </div>
                </div>

                <button class="mt-6 bg-[#00c2cb] text-white px-12 py-2.5 rounded-full font-bold text-sm shadow-md hover:bg-[#00acc1] hover:scale-105 transition-all duration-300">
                    Descargar PDF
                </button>

            </div>

        </div>
    </div>

  </div>
</template>