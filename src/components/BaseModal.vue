<script setup>
defineProps({
  show: Boolean
})
defineEmits(['close'])
</script>

<style scoped>
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

.modal-enter-active .relative,
.modal-leave-active .relative {
  transition: all 0.3s ease;
}

.modal-enter-from .relative,
.modal-leave-to .relative {
  transform: scale(0.95) translateY(-20px);
  opacity: 0;
}

@keyframes modal-appear {
  from {
    transform: scale(0.9);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}

.animate-modal-appear {
  animation: modal-appear 0.3s ease-out;
}
</style>

<template>
  <Transition name="modal">
    <div v-if="show" class="fixed inset-0 z-50 overflow-y-auto">
      <!-- Overlay oscuro -->
      <div 
        class="fixed inset-0 bg-black bg-opacity-60 backdrop-blur-sm transition-opacity"
        @click="$emit('close')"
      ></div>
      
      <!-- Modal centrado -->
      <div class="flex min-h-screen items-center justify-center p-4">
        <div 
          class="relative bg-white rounded-2xl shadow-2xl w-full max-w-2xl transform transition-all animate-modal-appear"
          @click.stop
        >
          <!-- Header -->
          <div class="flex items-center justify-between p-6 border-b-2 border-gray-100 bg-gradient-to-r from-blue-50 to-indigo-50">
            <h3 class="text-2xl font-bold text-gray-900">
              <slot name="header">Modal</slot>
            </h3>
            <button
              @click="$emit('close')"
              class="text-gray-400 hover:text-gray-600 transition-colors hover:rotate-90 transform duration-200"
            >
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
              </svg>
            </button>
          </div>
          
          <!-- Body -->
          <div class="p-8">
            <slot></slot>
          </div>
          
          <!-- Footer -->
          <div v-if="$slots.footer" class="flex justify-end gap-3 p-6 border-t-2 border-gray-100 bg-gray-50">
            <slot name="footer"></slot>
          </div>
        </div>
      </div>
    </div>
  </Transition>
</template>

