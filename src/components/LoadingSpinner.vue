<script setup>
defineProps({
  message: {
    type: String,
    default: 'Cargando...'
  }
})
</script>
<template>
  <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
    <div class="bg-white rounded-xl p-8 shadow-2xl">
      <div class="flex flex-col items-center">
        <div class="animate-spin rounded-full h-16 w-16 border-b-4 border-blue-600"></div>
        <p class="mt-4 text-gray-700 font-semibold">{{ message }}</p>
      </div>
    </div>
  </div>
</template>