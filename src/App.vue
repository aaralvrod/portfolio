<script setup>
import { provide } from 'vue';
import Navbar from '@/components/Navbar.vue';
import cvData from '@/data/cv.json';

provide('cv', cvData);
</script>

<template>
  <div class="min-h-screen bg-bento-bg text-bento-text selection:bg-accent-blue selection:text-white pb-20 relative isolate">
    
    <!-- Ambient Spotlights -->
    <div class="fixed top-[-10%] left-[-20%] w-[600px] h-[600px] bg-accent-blue/10 rounded-full blur-[120px] pointer-events-none animate-spotlight"></div>
    <div class="fixed bottom-[-10%] right-[-20%] w-[500px] h-[500px] bg-accent-purple/10 rounded-full blur-[100px] pointer-events-none animate-spotlight" style="animation-delay: -5s;"></div>

    <!-- Navbar Container -->
    <div class="max-w-7xl mx-auto px-4 pt-6 relative z-50">
      <Navbar />
    </div>

    <!-- Main Grid Layout -->
    <main class="max-w-7xl mx-auto px-4 py-8 relative z-10">
      <router-view v-slot="{ Component }">
        <Transition 
          enter-active-class="transition-all duration-500 ease-out"
          enter-from-class="opacity-0 scale-95 blur-sm"
          enter-to-class="opacity-100 scale-100 blur-0"
          leave-active-class="transition-all duration-300 ease-in"
          leave-from-class="opacity-100 scale-100"
          leave-to-class="opacity-0 scale-95"
        >
          <component :is="Component" />
        </Transition>
      </router-view>
    </main>

    <!-- Simple Footer -->
    <footer class="max-w-7xl mx-auto px-4 py-8 text-center text-bento-subtext text-xs">
      <p>Designed by Aarón Álvarez using Vue 3 & Tailwind v4</p>
    </footer>
  </div>
</template>
