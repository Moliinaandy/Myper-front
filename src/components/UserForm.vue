<script setup>
import { ref, watch, computed } from 'vue'

const props = defineProps({
  user: Object,
  isEditing: Boolean
})

const emit = defineEmits(['save', 'cancel'])

// Datos locales del formulario
const formData = ref({
  name: '',
  username: '',
  email: '',
  phone: ''
})

// Validación simple de email
const isValidEmail = computed(() => {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email)
})

// Rellenar datos si estamos editando
watch(() => props.user, (newUser) => {
  if (newUser) {
    formData.value = { ...newUser }
  }
}, { immediate: true })

const handleSubmit = () => {
  if (isValidEmail.value && formData.value.name && formData.value.username) {
    emit('save', formData.value)
  }
}
</script>

<template>
  <form @submit.prevent="handleSubmit" class="space-y-4">
    
    <div>
      <label class="block text-sm font-medium text-gray-700">Nombre Completo</label>
      <input v-model="formData.name" type="text" required class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-blue-500 focus:border-blue-500" />
    </div>

    <div>
      <label class="block text-sm font-medium text-gray-700">Username</label>
      <input v-model="formData.username" type="text" required class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-blue-500 focus:border-blue-500" />
    </div>

    <div>
      <label class="block text-sm font-medium text-gray-700">Email</label>
      <input v-model="formData.email" type="email" required 
             :class="{'border-red-500': formData.email && !isValidEmail}"
             class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-blue-500 focus:border-blue-500" />
      <span v-if="formData.email && !isValidEmail" class="text-xs text-red-500">Formato de correo inválido</span>
    </div>

    <div>
      <label class="block text-sm font-medium text-gray-700">Teléfono</label>
      <input v-model="formData.phone" type="text" required class="mt-1 block w-full border border-gray-300 rounded-md shadow-sm p-2 focus:ring-blue-500 focus:border-blue-500" />
    </div>

    <div class="flex justify-end gap-3 mt-6">
      <button type="button" @click="$emit('cancel')" class="px-4 py-2 bg-gray-100 text-gray-700 rounded-lg hover:bg-gray-200">Cancelar</button>
      
      <button type="submit" :disabled="!isValidEmail" 
              class="px-4 py-2 bg-[#2563EB] text-white rounded-lg hover:bg-blue-700 disabled:opacity-50 disabled:cursor-not-allowed">
        {{ isEditing ? 'Guardar Cambios' : 'Crear Usuario' }}
      </button>
    </div>
  </form>
</template>