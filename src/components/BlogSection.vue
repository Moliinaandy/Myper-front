<script setup>
const posts = [
  {
    id: 1,
    title: 'IMPACTO DE LA IA EN SST',
    date: '31 ENERO 2026',
    image: 'https://images.unsplash.com/photo-1555949963-ff9fe0c870eb?auto=format&fit=crop&q=80&w=400', 
    category: 'Tecnología'
  },
  {
    id: 2,
    title: '5 SEÑALES DE DIGITALIZACIÓN',
    date: '11 DICIEMBRE 2025',
    image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&q=80&w=400',
    category: 'Gestión'
  },
  {
    id: 3,
    title: 'LEY 30012 Y MYPER',
    date: '15 NOVIEMBRE 2025',
    image: 'https://images.unsplash.com/photo-1589829085413-56de8ae18c73?auto=format&fit=crop&q=80&w=400',
    category: 'Legal'
  }
]
</script>

<template>
  <section class="bg-slate-50 py-20 font-sans border-t border-gray-200">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <div class="flex flex-col md:flex-row items-center justify-between mb-16">
        <div class="max-w-xl">
           <h2 class="text-blue-500 font-bold tracking-wide uppercase text-sm mb-2">¡Bienvenido al</h2>
           <h3 class="text-4xl font-extrabold text-[#06b6d4] mb-4">Blog de Myper!</h3>
           <p class="text-gray-600">Descubre las últimas tendencias, consejos y novedades en software empresarial.</p>
        </div>
        <div class="hidden md:block">
            <div class="w-48 h-32 bg-gradient-to-r from-blue-200 to-cyan-200 rounded-2xl shadow-inner flex items-center justify-center transform rotate-3 hover:rotate-6 transition">
                <span class="text-blue-500 font-bold text-4xl">BLOG</span>
            </div>
        </div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-3 gap-10">
        
        <div class="lg:col-span-2 space-y-8">
          <article v-for="post in posts" :key="post.id" class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden hover:shadow-md transition-shadow flex flex-col sm:flex-row h-full sm:h-52 group cursor-pointer">
            
            <div class="w-full sm:w-2/5 bg-gray-100 relative overflow-hidden">
                <img 
                  :src="post.image" 
                  :alt="post.title" 
                  class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                />
            </div>
            
            <div class="p-6 sm:w-3/5 flex flex-col justify-center items-start">
               <span class="text-xs font-bold text-gray-400 uppercase mb-1">{{ post.category }}</span>
               
               <h4 class="text-gray-800 font-bold text-lg leading-snug mb-4 group-hover:text-blue-600 transition-colors uppercase">
                 {{ post.title }}
               </h4>
               
               <span class="inline-block bg-[#06b6d4] text-white text-xs font-bold px-3 py-1 rounded-full shadow-sm">
                 {{ post.date }}
               </span>
            </div>
          </article>
        </div>

        <div class="space-y-8">
            <div class="bg-white p-6 rounded-3xl shadow-lg border border-gray-50">
               <h4 class="font-bold text-gray-800 text-center mb-4">Suscríbete</h4>
               <form class="space-y-3">
                  <input type="email" placeholder="Correo electrónico" class="w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-cyan-400 outline-none text-sm bg-gray-50" />
                  <button class="w-full bg-[#06b6d4] hover:bg-cyan-500 text-white font-bold py-3 rounded-xl transition shadow-md">
                      Suscribirme
                  </button>
               </form>
            </div>

            <div class="bg-[#2563EB] rounded-3xl p-8 text-center relative overflow-hidden group shadow-lg">
                <div class="relative z-10">
                    <h4 class="text-white font-bold text-xl mb-6">¡Únete a la transformación digital!</h4>
                    <div class="w-20 h-20 mx-auto bg-white/10 rounded-full flex items-center justify-center backdrop-blur-sm border border-white/20">
                        <span class="text-3xl">🚀</span>
                    </div>
                </div>
            </div>
        </div>

      </div>
    </div>
  </section>
</template>