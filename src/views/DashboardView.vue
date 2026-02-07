<script setup>
import { ref, computed, onMounted } from 'vue'
import UserTable from '../components/UserTable.vue'
import UserForm from '../components/UserForm.vue'
import LoadingSpinner from '../components/LoadingSpinner.vue'
import BaseModal from '../components/BaseModal.vue'


const users = ref([])
const logs = ref([]) 
const loading = ref(true)
const searchQuery = ref('')
const showForm = ref(false)
const showDeleteConfirm = ref(false)
const isEditing = ref(false)
const selectedUser = ref(null)
const userToDeleteId = ref(null)
const toast = ref({ show: false, message: '', type: 'success' })

const filteredUsers = computed(() => {
  if (!searchQuery.value) return users.value
  const query = searchQuery.value.toLowerCase()
  return users.value.filter(user => 
    user.name.toLowerCase().includes(query) || 
    user.email.toLowerCase().includes(query)
  )
})

const fetchUsers = async () => {
  loading.value = true
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/users')
    users.value = await res.json()
    addLog('Sistema', 'Usuarios cargados desde API')
  } catch (e) { 
    showToast('Error de conexión', 'error') 
  } finally { 
    loading.value = false 
  }
}

onMounted(() => { fetchUsers() })


const addLog = (user, action) => {
  const time = new Date().toLocaleTimeString('es-PE', { hour: '2-digit', minute: '2-digit' })
  logs.value.unshift({ id: Date.now(), user, action, time })
}

const openNewUserForm = () => { 
    isEditing.value = false; 
    selectedUser.value = { name: '', username: '', email: '', phone: '' }; 
    showForm.value = true;
  }

const openEditUserForm = (user) => { 
    isEditing.value = true; 
    selectedUser.value = { ...user }; 
    showForm.value = true;
}

const handleSaveUser = (userData) => {
  if (isEditing.value) {
    //busqueda 
    const index = users.value.findIndex(u => u.id === userData.id)
    if (index !== -1) users.value[index] = userData
    
    addLog('Admin', `Editó usuario: ${userData.username}`)
    showToast('Usuario actualizado correctamente')
  } else {
//id  automaticamente incrementable
    const newId = users.value.length ? Math.max(...users.value.map(u => u.id)) + 1 : 1
    users.value.push({ ...userData, id: newId })
    
    addLog('Admin', `Creó usuario: ${userData.username}`)
    showToast('Usuario creado correctamente')
  }
  showForm.value = false
}


const confirmDelete = (id) => { userToDeleteId.value = id; showDeleteConfirm.value = true }
const executeDelete = () => {
  const user = users.value.find(u => u.id === userToDeleteId.value)
  users.value = users.value.filter(u => u.id !== userToDeleteId.value)
  
  addLog('Admin', `Eliminó usuario: ${user?.username}`)
  showDeleteConfirm.value = false
  showToast('Usuario eliminado')
}

const showToast = (message, type = 'success') => { toast.value = { show: true, message, type }; setTimeout(() => (toast.value.show = false), 3000) }
</script>

<template>
  <div class="py-10 bg-[#f8fafc] min-h-screen">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        
        <div class="mb-8">
            <h2 class="text-3xl font-extrabold text-gray-900">Gestión de Usuarios</h2>
            <p class="text-gray-500 mt-1">Panel de usuarios</p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-4 gap-8">
            
            <div class="lg:col-span-3">
                <div class="bg-white rounded-xl shadow-sm border border-gray-100 overflow-hidden p-6">
                    
                    <div class="flex flex-col sm:flex-row justify-between gap-4 mb-6">
                        <input v-model="searchQuery" type="text" placeholder="Buscar por nombre o email..." class="border border-gray-200 rounded-lg px-4 py-2 w-full sm:w-64 focus:ring-2 focus:ring-blue-500 outline-none" />
                        
                        <button @click="openNewUserForm" class="bg-[#2563EB] hover:bg-blue-700 text-white px-6 py-2 rounded-lg font-bold transition flex items-center gap-2 justify-center">
                            <span>+</span> Nuevo Usuario
                        </button>
                    </div>

                    <div class="min-h-[300px]">
                        <LoadingSpinner v-if="loading" class="py-10" />
                        <UserTable v-else :users="filteredUsers" @edit="openEditUserForm" @delete="confirmDelete" />
                    </div>
                    
                    <div class="mt-4 text-sm text-gray-500 text-right">
                        Total registros: {{ users.length }}
                    </div>
                </div>
            </div>

            <div class="lg:col-span-1">
                <div class="bg-white rounded-xl shadow-sm border border-gray-100 p-6 sticky top-24">
                    <h3 class="font-bold text-gray-800 mb-4 border-b pb-2">Historial de Cambios</h3>
                    <div class="space-y-4 max-h-[500px] overflow-y-auto">
                        <div v-if="logs.length === 0" class="text-sm text-gray-400 italic">Sin actividad reciente.</div>
                        <div v-for="log in logs" :key="log.id" class="text-sm">
                            <p class="font-medium text-gray-800">{{ log.action }}</p>
                            <div class="flex justify-between text-xs text-gray-400 mt-1">
                                <span>{{ log.user }}</span>
                                <span>{{ log.time }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </div>

    <BaseModal :show="showForm" @close="showForm = false">
      <template #header>{{ isEditing ? 'Editar' : 'Crear' }} Usuario</template>
      <UserForm :user="selectedUser" :isEditing="isEditing" @save="handleSaveUser" @cancel="showForm = false" />
    </BaseModal>

    <BaseModal :show="showDeleteConfirm" @close="showDeleteConfirm = false">
       <div class="p-6 text-center">
         <h3 class="text-lg font-bold mb-2 text-gray-900">¿Eliminar este usuario?</h3>
         <p class="text-gray-500 mb-6">Esta acción eliminará al usuario de la lista localmente.</p>
         <div class="flex justify-center gap-4">
            <button @click="showDeleteConfirm = false" class="px-4 py-2 border rounded-lg hover:bg-gray-50">Cancelar</button>
            <button @click="executeDelete" class="px-4 py-2 bg-red-600 text-white rounded-lg hover:bg-red-700 font-bold">Sí, Eliminar</button>
         </div>
      </div>
    </BaseModal>

    <Transition name="toast">
      <div v-if="toast.show" class="fixed bottom-6 right-6 z-50 bg-gray-800 text-white px-6 py-3 rounded-lg shadow-xl font-medium">
        {{ toast.message }}
      </div>
    </Transition>
  </div>
</template>