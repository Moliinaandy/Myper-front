<script setup>
defineProps({
  users: Array,
})

// Definimos los eventos que enviaremos al padre
const emit = defineEmits(['edit', 'delete'])
</script>

<template>
  <div class="bg-white rounded-2xl shadow-xl overflow-hidden border border-gray-100">
    
    <div class="bg-gradient-to-r from-blue-600 to-indigo-600 px-6 py-5">
      <h2 class="text-xl font-bold text-white flex items-center gap-3">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z" />
        </svg>
        Lista de Usuarios ({{ users.length }})
      </h2>
    </div>

    <div class="overflow-x-auto">
      <table class="w-full">
        <thead class="bg-gray-50 border-b-2 border-gray-200">
          <tr>
            <th class="px-6 py-4 text-left text-xs font-bold text-gray-500 uppercase tracking-wider">ID</th>
            <th class="px-6 py-4 text-left text-xs font-bold text-gray-500 uppercase tracking-wider">Usuario</th>
            <th class="px-6 py-4 text-left text-xs font-bold text-gray-500 uppercase tracking-wider">Contacto</th>
            <th class="px-6 py-4 text-center text-xs font-bold text-gray-500 uppercase tracking-wider">Acciones</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-gray-200 bg-white">
          <tr 
            v-for="user in users" 
            :key="user.id"
            class="hover:bg-blue-50 transition-all duration-200"
          >
            <td class="px-6 py-5 whitespace-nowrap">
              <span class="inline-flex items-center justify-center w-8 h-8 bg-gray-100 rounded-full font-bold text-gray-600 text-xs">
                {{ user.id }}
              </span>
            </td>

            <td class="px-6 py-5">
              <div class="flex items-center gap-4">
                <div class="flex-shrink-0 w-10 h-10 bg-gradient-to-br from-blue-400 to-indigo-500 rounded-full flex items-center justify-center shadow-md text-white font-bold">
                  {{ user.name.charAt(0) }}
                </div>
                <div>
                  <div class="text-sm font-bold text-gray-900">{{ user.name }}</div>
                  <div class="text-xs text-blue-500 font-medium">@{{ user.username }}</div>
                </div>
              </div>
            </td>

            <td class="px-6 py-5">
              <div class="flex flex-col gap-1">
                <div class="flex items-center gap-2 text-sm text-gray-600">
                  <svg class="w-4 h-4 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" /></svg>
                  {{ user.email }}
                </div>
                <div class="flex items-center gap-2 text-sm text-gray-600">
                  <svg class="w-4 h-4 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" /></svg>
                  {{ user.phone }}
                </div>
              </div>
            </td>

            <td class="px-6 py-5">
              <div class="flex justify-center gap-3">
                <button 
                  @click="$emit('edit', user)" 
                  class="px-3 py-1.5 bg-yellow-500 text-white rounded-lg hover:bg-yellow-600 transition shadow-sm hover:shadow-md font-bold text-xs flex items-center gap-1"
                >
                  <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" /></svg>
                  EDITAR
                </button>
                
                <button 
                  @click="$emit('delete', user.id)" 
                  class="px-3 py-1.5 bg-red-500 text-white rounded-lg hover:bg-red-600 transition shadow-sm hover:shadow-md font-bold text-xs flex items-center gap-1"
                >
                  <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" /></svg>
                  ELIMINAR
                </button>
              </div>
            </td>
          </tr>

          <tr v-if="users.length === 0">
            <td colspan="4" class="px-6 py-12 text-center text-gray-500">
               No hay usuarios registrados.
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>