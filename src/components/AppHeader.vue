<script setup>
import { ref } from 'vue'

const props = defineProps({
  isAuthenticated: Boolean
})

const emit = defineEmits(['navigate', 'logout'])

const menuItems = [
  { name: 'Soluciones', view: 'solutions' },
  { name: 'Acerca de', view: 'home' }, 
  { name: 'Recursos', view: 'resources' },
  { name: 'Contacto', view: 'contact' }, 
  { name: 'Blog', view: 'blog' },
]

const isMobileMenuOpen = ref(false)
</script>

<template>
  <header class="bg-white sticky top-0 z-50 font-sans border-b border-gray-100 shadow-sm">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-20">
        
        <div class="flex-shrink-0 flex items-center gap-1 cursor-pointer hover:opacity-80 transition" @click="$emit('navigate', 'home')">
          <span class="text-3xl font-extrabold text-[#2563EB] tracking-tighter">M</span>
          <span class="text-3xl font-extrabold text-[#06b6d4] tracking-tighter">YPER</span>
        </div>

        <nav class="hidden md:flex space-x-8 items-center">
          
          <a v-for="item in menuItems" 
             :key="item.name" 
             href="#"
             @click.prevent="$emit('navigate', item.view)" 
             class="text-gray-500 hover:text-blue-600 font-medium transition-colors text-sm uppercase">
            {{ item.name }}
          </a>

          <div class="flex items-center gap-4 border-l pl-6 border-gray-200 ml-4">
            
            <template v-if="isAuthenticated">
                <button 
                   @click="$emit('navigate', 'dashboard')"
                   class="text-blue-600 hover:text-blue-800 font-bold transition-colors text-sm uppercase bg-blue-50 px-4 py-2 rounded-lg">
                   Panel
                </button>
                
                <button 
                   @click="$emit('logout')"
                   class="text-red-400 hover:text-red-600 font-medium transition-colors text-sm uppercase">
                   Salir
                </button>
            </template>

            <template v-else>
                <button 
                   @click="$emit('navigate', 'login')"
                   class="text-gray-500 hover:text-[#2563EB] font-bold transition-colors text-sm uppercase">
                   Ingresar
                </button>
            </template>

          </div>
          
          <button class="bg-[#06b6d4] hover:bg-cyan-500 text-white px-6 py-2.5 rounded-full font-bold text-sm shadow-md transition-all ml-4">
            Reservar Demo
          </button>
        </nav>

        <div class="md:hidden flex items-center">
          <button @click="isMobileMenuOpen = !isMobileMenuOpen" class="text-gray-600 p-2">
            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
          </button>
        </div>
      </div>
    </div>
  </header>
</template>