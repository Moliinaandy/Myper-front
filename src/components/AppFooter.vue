<template>
  <footer class="bg-[#1a237e] text-white pt-16 pb-8 font-sans relative overflow-hidden">
    <div class="absolute top-0 left-0 w-full h-2 bg-gradient-to-r from-blue-500 via-cyan-400 to-blue-500"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-10 mb-16 text-sm">
        
        <div>
          <h3 class="text-lg font-bold mb-6 text-white">Menú</h3>
          <ul class="space-y-3 text-blue-100">
            <li><a href="#" class="hover:text-cyan-300 transition">Nosotros</a></li>
            <li><a href="#" class="hover:text-cyan-300 transition">Sostenibilidad</a></li>
            <li><a href="#" class="hover:text-cyan-300 transition">Eventos</a></li>
            <li><a href="#" class="hover:text-cyan-300 transition">Recursos</a></li>
            <li><a href="#" class="hover:text-cyan-300 transition">Contacto</a></li>
            <li><a href="#" class="hover:text-cyan-300 transition">Blog</a></li>
          </ul>
        </div>

        <div>
          <h3 class="text-lg font-bold mb-6 text-[#06b6d4]">Soluciones</h3>
          
          <h4 class="font-bold text-white mb-3 uppercase text-xs tracking-wider">MYPER SSOMA</h4>
          <ul class="space-y-2 text-blue-100 mb-8">
            <li>Cronograma y planes SSST</li>
            <li>Capacitaciones, inspecciones y más</li>
            <li>Estadísticas SST y Matriz IPERC</li>
            <li>Seguimiento a medidas correctivas</li>
          </ul>

          <h4 class="font-bold text-white mb-3 uppercase text-xs tracking-wider">SERVICIO</h4>
          <ul class="space-y-2 text-blue-100">
            <li>Desarrollo de software a medida</li>
            <li>Servicio de soporte remoto</li>
          </ul>
        </div>

        <div>
          <div class="h-8 md:block hidden"></div> <h4 class="font-bold text-white mb-3 uppercase text-xs tracking-wider mt-5">MYPER GP</h4>
          <ul class="space-y-2 text-blue-100">
            <li>Gestión de proveedores</li>
            <li>Homologación de proveedores</li>
            <li>Ordenes y comprobantes de pago</li>
            <li>Programación de visitas</li>
          </ul>
        </div>

        <div>
          <h3 class="text-lg font-bold mb-6 text-[#06b6d4]">Contacto</h3>
          <div class="space-y-4 text-blue-100">
            <p class="hover:text-white cursor-pointer">ventas@myper.com.pe</p>
            <p class="font-bold text-white text-lg">(+51) 959 712 122</p>
            <p class="leading-relaxed opacity-90">
              Calle Luis Felipe<br>
              Villarán 362 - San<br>
              Isidro, Lima, Perú.
            </p>
          </div>
        </div>
      </div>

      <div class="mb-12 border-b border-blue-900/50 pb-12">
        <button class="bg-[#06b6d4] hover:bg-cyan-500 text-white px-8 py-3 rounded-full font-bold shadow-lg transition-transform transform hover:-translate-y-1">
          Reservar Demo
        </button>
      </div>

      <div class="flex flex-col md:flex-row justify-between items-center gap-6 pt-4">
        
        <div class="flex items-center gap-1 opacity-90">
           <span class="text-2xl font-extrabold text-blue-400">M</span>
           <span class="text-2xl font-extrabold text-white">YPER</span>
        </div>

        <p class="text-xs text-blue-200">
          ¡Únete a la transformación digital! &nbsp; © Myper 2026
        </p>

        <div class="flex space-x-3">
          <a href="#" class="bg-white text-[#1a237e] p-2 rounded-full hover:bg-[#06b6d4] hover:text-white transition w-8 h-8 flex items-center justify-center">
            <span class="font-bold">f</span>
          </a>
          <a href="#" class="bg-white text-[#1a237e] p-2 rounded-full hover:bg-red-500 hover:text-white transition w-8 h-8 flex items-center justify-center">
             <span class="font-bold">YT</span>
          </a>
          <a href="#" class="bg-white text-[#1a237e] p-2 rounded-full hover:bg-pink-600 hover:text-white transition w-8 h-8 flex items-center justify-center">
             <span class="font-bold">in</span>
          </a>
          <a href="#" class="bg-white text-[#1a237e] p-2 rounded-full hover:bg-blue-600 hover:text-white transition w-8 h-8 flex items-center justify-center">
             <span class="font-bold">Ln</span>
          </a>
        </div>
      </div>

      <a href="#" class="fixed bottom-6 right-6 z-50 bg-[#25D366] text-white p-3 rounded-full shadow-xl hover:bg-green-600 transition-all hover:scale-110 flex items-center justify-center">
        <svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24"><path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.711 2.592 2.664-.698c.969.587 1.961.943 3.218.943 3.382 0 5.768-2.587 5.768-5.766-.001-3.187-2.375-5.124-6.19-5.124z"></path><path d="M12.04 2C6.496 2 2 6.494 2 12.04c0 1.937.543 3.732 1.48 5.257L2 22l4.87-1.391c1.474.841 3.211 1.346 5.17 1.346 5.545 0 10.04-4.495 10.04-10.04C22.08 6.495 17.585 2 12.04 2z"></path></svg>
      </a>

    </div>
  </footer>
</template>