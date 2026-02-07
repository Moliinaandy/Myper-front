<script setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')
const error = ref(false)
const emit = defineEmits(['success'])

const handleLogin = () => {
  if (email.value === 'admin@myper.com' && password.value === 'Andrea27') {
    error.value = false
    emit('success') 
  } else {
    error.value = true 
  }
}
</script>

<template>
  <div class="min-h-screen flex items-center justify-center bg-gray-50 py-12 px-4 sm:px-6 lg:px-8 font-sans">
    
    <div class="max-w-4xl w-full space-y-8 bg-white rounded-2xl shadow-xl overflow-hidden flex">
        
        <div class="hidden md:block w-1/2 bg-cover bg-center" style="background-image: url('https://images.unsplash.com/photo-1542744173-8e7e53415bb0?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80');">
            <div class="h-full w-full bg-blue-900/40 backdrop-blur-[2px] flex items-center justify-center">
                <div class="text-white text-center p-10">
                    <h2 class="text-3xl font-extrabold mb-2">Bienvenido a MYPER</h2>
                    <p class="text-blue-100">Gestión inteligente para empresas modernas.</p>
                </div>
            </div>
        </div>

        <div class="w-full md:w-1/2 p-10 flex flex-col justify-center">
            
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold text-gray-900">Iniciar Sesión</h2>
                <p class="mt-2 text-sm text-gray-600">
                    Accede al panel de administración
                </p>
            </div>

            <form class="space-y-6" @submit.prevent="handleLogin">
                
                <div>
                    <label class="block text-sm font-medium text-gray-700">Correo Electrónico</label>
                    <div class="mt-1">
                        <input v-model="email" type="email" required 
                            class="appearance-none block w-full px-3 py-3 border border-gray-300 rounded-lg shadow-sm placeholder-gray-400 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" 
                            placeholder="admin@myper.com">
                    </div>
                </div>

                <div>
                    <label class="block text-sm font-medium text-gray-700">Contraseña</label>
                    <div class="mt-1">
                        <input v-model="password" type="password" required 
                            class="appearance-none block w-full px-3 py-3 border border-gray-300 rounded-lg shadow-sm placeholder-gray-400 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" 
                            placeholder="••••••">
                    </div>
                </div>

                <div v-if="error" class="bg-red-50 text-red-600 text-sm p-3 rounded-lg flex items-center gap-2">
                    <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" /></svg>
                    Credenciales incorrectas
                </div>

                <div>
                    <button type="submit" class="w-full flex justify-center py-3 px-4 border border-transparent rounded-lg shadow-sm text-sm font-medium text-white bg-[#06b6d4] hover:bg-cyan-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-cyan-500 transition-colors">
                        Ingresar al Sistema
                    </button>
                </div>
            </form>
            
            <div class="mt-6 text-center text-xs text-gray-400">
                &copy; 2026 Myper Inc. Todos los derechos reservados.
            </div>

        </div>
    </div>
  </div>
</template>