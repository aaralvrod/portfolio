<template>
  <nav class="glass-panel rounded-[2rem] px-2 py-2 flex items-center justify-between mx-auto max-w-2xl sticky top-6 z-50 shadow-2xl shadow-black/50">
    
    <!-- Home / Logo -->
    <router-link 
      to="/" 
      class="w-10 h-10 flex items-center justify-center rounded-full bg-bento-card hover:bg-white/10 transition-colors"
    >
      <span class="font-bold text-white">A</span>
    </router-link>

    <!-- Links -->
    <div class="flex items-center gap-1">
      <router-link 
        v-for="item in navItems" 
        :key="item.path"
        :to="item.path"
        class="px-5 py-2 text-sm font-medium text-bento-subtext hover:text-white transition-colors rounded-full"
        active-class="bg-white/10 text-white shadow-inner"
      >
        {{ item.label }}
      </router-link>
    </div>

    <!-- Contact -->
    <a 
      href="mailto:aaralvrod@gmail.com"
      class="w-10 h-10 flex items-center justify-center rounded-full bg-apple-blue hover:bg-blue-500 transition-colors text-white"
      title="Contactar"
    >
      <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
      </svg>
    </a>
  </nav>
</template>

<script setup>
import { reactive } from 'vue';

const navItems = [
  { label: 'Home', path: '/' },
  { label: 'Proyectos', path: '/proyectos' },
];
</script>
