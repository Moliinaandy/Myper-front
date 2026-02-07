<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  message: ''
})

const handleSubmit = () => {
  alert(`¡Gracias ${form.value.name}! Hemos recibido tu mensaje.`)
  form.value = { name: '', email: '', message: '' }
}
</script>

<template>
  <div class="pt-24 pb-20 bg-white min-h-screen font-sans">
    
    <div class="max-w-5xl mx-auto px-6">
        
        <div class="text-center mb-16">
            <h1 class="text-4xl font-extrabold text-[#06b6d4] mb-4">Contáctanos</h1>
            <p class="text-gray-500 text-lg">
                ¿Tienes alguna duda o quieres una demo? Escríbenos.
            </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-start">
            
            <div class="bg-slate-50 p-8 rounded-3xl border border-gray-100 shadow-sm">
                <h3 class="text-2xl font-bold text-gray-800 mb-8">Nuestros Canales</h3>
                
                <div class="space-y-8">
                    <div class="flex items-start gap-4">
                        <div class="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center text-blue-600 shrink-0">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" /></svg>
                        </div>
                        <div>
                            <p class="font-bold text-gray-900">Llámanos</p>
                            <p class="text-gray-600 text-sm">+51 987 654 321</p>
                            <p class="text-gray-600 text-sm">+51 (01) 123 4567</p>
                        </div>
                    </div>

                    <div class="flex items-start gap-4">
                        <div class="w-12 h-12 bg-cyan-100 rounded-full flex items-center justify-center text-[#06b6d4] shrink-0">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" /></svg>
                        </div>
                        <div>
                            <p class="font-bold text-gray-900">Escríbenos</p>
                            <p class="text-gray-600 text-sm">contacto@myper.com</p>
                            <p class="text-gray-600 text-sm">soporte@myper.com</p>
                        </div>
                    </div>

                    <div class="flex items-start gap-4">
                        <div class="w-12 h-12 bg-indigo-100 rounded-full flex items-center justify-center text-indigo-600 shrink-0">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" /><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" /></svg>
                        </div>
                        <div>
                            <p class="font-bold text-gray-900">Visítanos</p>
                            <p class="text-gray-600 text-sm">Av. Empresarial 123, Of. 405</p>
                            <p class="text-gray-600 text-sm">San Isidro, Lima - Perú</p>
                        </div>
                    </div>
                </div>
            </div>

            <form @submit.prevent="handleSubmit" class="bg-white space-y-6">
                
                <div>
                    <label class="block text-sm font-bold text-gray-700 mb-2">Nombre Completo</label>
                    <input 
                        v-model="form.name" 
                        type="text" 
                        required
                        class="w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-cyan-400 focus:ring-2 focus:ring-cyan-100 outline-none transition bg-gray-50"
                        placeholder="Ej: Juan Molina"
                    />
                </div>

                <div>
                    <label class="block text-sm font-bold text-gray-700 mb-2">Correo Electrónico</label>
                    <input 
                        v-model="form.email" 
                        type="email" 
                        required
                        class="w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-cyan-400 focus:ring-2 focus:ring-cyan-100 outline-none transition bg-gray-50"
                        placeholder="tu@correo.com"
                    />
                </div>

                <div>
                    <label class="block text-sm font-bold text-gray-700 mb-2">Mensaje</label>
                    <textarea 
                        v-model="form.message" 
                        rows="4" 
                        required
                        class="w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-cyan-400 focus:ring-2 focus:ring-cyan-100 outline-none transition bg-gray-50 resize-none"
                        placeholder="Cuéntanos en qué podemos ayudarte..."
                    ></textarea>
                </div>

                <button 
                    type="submit" 
                    class="w-full bg-[#06b6d4] hover:bg-cyan-600 text-white font-bold py-4 rounded-xl shadow-lg hover:shadow-xl transition-all transform hover:-translate-y-1"
                >
                    Enviar Mensaje
                </button>
            </form>

        </div>
    </div>
  </div>
</template>