<script setup>
import { ref } from 'vue'
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import HomeView from './views/HomeView.vue'
import DashboardView from './views/DashboardView.vue'
import BlogView from './views/BlogView.vue' 
import SolutionsView from './views/SolutionsView.vue'
import ResourcesView from './views/ResourcesView.vue'
import LoginView from './views/LoginView.vue' 
import ContactView from './views/ContactoView.vue'

const currentView = ref('home')
const isAuthenticated = ref(false)
const navigateTo = (viewName) => {
  if (viewName === 'dashboard' && !isAuthenticated.value) {
    currentView.value = 'login'
  } else {
    currentView.value = viewName
  }
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

const onLoginSuccess = () => {
  isAuthenticated.value = true
  currentView.value = 'dashboard'
}

const logout = () => {
  isAuthenticated.value = false
  currentView.value = 'home' 
}
</script>

<template>
  <div class="min-h-screen flex flex-col font-sans text-slate-800 bg-white">
    
   <AppHeader 
        v-if="currentView !== 'login'" 
        :isAuthenticated="isAuthenticated" 
        @navigate="navigateTo" 
        @logout="logout"
    />

    <main class="flex-grow">
      <Transition name="fade" mode="out-in">
        <HomeView v-if="currentView === 'home'" />
        <BlogView v-else-if="currentView === 'blog'" />
        <SolutionsView v-else-if="currentView === 'solutions'" />
        <ResourcesView v-else-if="currentView === 'resources'" />
        <LoginView v-else-if="currentView === 'login'" @success="onLoginSuccess" />
        <DashboardView v-else-if="currentView === 'dashboard'" />
        <ContactView v-else-if="currentView === 'contact'" />
      </Transition>
    </main>

    <AppFooter v-if="currentView !== 'login'" />

  </div>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>