<script setup>
import { ref } from 'vue'

const solutions = [
  {
    id: 1,
    title: 'Gestión de SSOMA',
    description: 'Plataforma especializada en Seguridad y Salud en el Trabajo (SST). Asegura el cumplimiento con Sunafil y la normativa 29783.',
    image: 'https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?auto=format&fit=crop&q=80&w=800',
    color: 'blue', 
    features: [
      'Cronograma y planes de SST',
      'Capacitaciones e inspecciones',
      'Estadísticas SST y Matriz IPERC',
      'Seguimiento a medidas correctivas'
    ]
  },
  {
    id: 2,
    title: 'Gestión de Proveedores',
    description: 'Optimiza la relación con tus socios estratégicos. Centraliza la información, agiliza pagos y garantiza el cumplimiento de estándares.',
    image: 'https://images.unsplash.com/photo-1454165804606-c3d57bc86b40?auto=format&fit=crop&q=80&w=800',
    color: 'indigo',
    features: [
      'Homologación de proveedores',
      'Gestión de facturas y pagos',
      'Programación de visitas',
      'Evaluación de desempeño'
    ]
  },
  {
    id: 3,
    title: 'Gestión de Mantenimiento (MP)',
    description: 'Maximiza la vida útil de tus activos. Planifica mantenimientos preventivos y correctivos para evitar paradas inesperadas.',
    image: 'https://images.unsplash.com/photo-1581092160562-40aa08e78837?auto=format&fit=crop&q=80&w=800',
    color: 'emerald', 
    features: [
      'Plan de Mantenimiento Preventivo',
      'Órdenes de trabajo (OT)',
      'Historial de maquinaria',
      'Control de repuestos e inventario'
    ]
  },
  {
    id: 4,
    title: 'Gestión de Servicios',
    description: 'Eleva la calidad de atención. Gestiona tickets, solicitudes y mesa de ayuda para garantizar la satisfacción del cliente interno o externo.',
    image: 'https://images.unsplash.com/photo-1556745757-8d76bdb6984b?auto=format&fit=crop&q=80&w=800',
    color: 'violet', 
    features: [
      'Mesa de ayuda (Help Desk)',
      'Gestión de Tickets y SLA',
      'Encuestas de satisfacción',
      'Reportes de atención'
    ]
  }
]

// Función auxiliar para clases de color dinámicas
const getHeaderColor = (color) => {
  const colors = {
    blue: 'bg-blue-100 from-blue-600 to-cyan-500',
    indigo: 'bg-indigo-100 from-indigo-600 to-blue-500',
    emerald: 'bg-emerald-100 from-emerald-600 to-teal-500',
    violet: 'bg-violet-100 from-violet-600 to-fuchsia-500'
  }
  return colors[color] || colors.blue
}

const getTitleColor = (color) => {
  const colors = {
    blue: 'text-blue-800',
    indigo: 'text-indigo-800',
    emerald: 'text-emerald-800',
    violet: 'text-violet-800'
  }
  return colors[color] || 'text-gray-800'
}

const getCheckColor = (color) => {
    const colors = {
    blue: 'text-cyan-500',
    indigo: 'text-indigo-500',
    emerald: 'text-emerald-500',
    violet: 'text-violet-500'
  }
  return colors[color] || 'text-cyan-500'
}

const getBoxColor = (color) => {
    const colors = {
    blue: 'bg-blue-50 border-blue-100 text-blue-900',
    indigo: 'bg-indigo-50 border-indigo-100 text-indigo-900',
    emerald: 'bg-emerald-50 border-emerald-100 text-emerald-900',
    violet: 'bg-violet-50 border-violet-100 text-violet-900'
  }
  return colors[color] || 'bg-gray-50'
}
</script>

<template>
  <div class="pt-24 pb-24 bg-slate-50 min-h-screen font-sans">
    
    <div class="text-center px-4 mb-20">
        <h1 class="text-4xl md:text-6xl font-extrabold text-[#06b6d4] mb-6 tracking-tight">
            Nuestras Soluciones
        </h1>
        <p class="text-gray-500 text-lg md:text-xl max-w-3xl mx-auto leading-relaxed">
            Tecnología especializada para simplificar la gestión humana, optimizar recursos y garantizar la seguridad de tu equipo.
        </p>
    </div>
    
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-6xl mx-auto px-6">
        
        <div v-for="sol in solutions" :key="sol.id" 
             class="bg-white rounded-[2rem] shadow-lg border border-gray-100 overflow-hidden hover:shadow-2xl hover:-translate-y-2 transition-all duration-300 group flex flex-col h-full">
            
            <div :class="`h-60 relative overflow-hidden ${getHeaderColor(sol.color).split(' ')[0]}`">
                <div :class="`absolute inset-0 bg-gradient-to-br ${getHeaderColor(sol.color).split(' ').slice(1).join(' ')} opacity-0 group-hover:opacity-20 transition-opacity duration-500 z-10`"></div>
                
                <img 
                  :src="sol.image" 
                  :alt="sol.title" 
                  class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110" 
                />
            </div>

            <div class="p-8 flex flex-col flex-grow">
                <h3 :class="`text-2xl font-extrabold italic mb-4 ${getTitleColor(sol.color)}`">
                    {{ sol.title }}
                </h3>
                
                <p class="text-gray-600 mb-8 leading-relaxed flex-grow">
                    {{ sol.description }}
                </p>

                <div :class="`rounded-2xl p-6 border ${getBoxColor(sol.color)}`">
                    <p class="font-bold mb-4 text-xs uppercase tracking-widest opacity-80">Funciones clave:</p>
                    <ul class="space-y-3">
                        <li v-for="(feature, index) in sol.features" :key="index" class="flex items-start gap-3 text-gray-700 text-sm font-medium">
                            <span :class="`mt-0.5 text-lg ${getCheckColor(sol.color)}`">✓</span> 
                            {{ feature }}
                        </li>
                    </ul>
                </div>
            </div>
        </div>

    </div>
  </div>
</template>