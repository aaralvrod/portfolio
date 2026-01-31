<template>
  <div class="space-y-8">
    <!-- Header -->
    <div class="relative overflow-hidden rounded-2xl bg-gradient-to-br from-indigo-900/50 via-purple-900/30 to-black border border-white/10 p-8 md:p-10">
      <div class="absolute top-0 right-0 w-64 h-64 bg-indigo-500/20 rounded-full blur-3xl -translate-y-1/2 translate-x-1/2" />
      <div class="absolute bottom-0 left-0 w-48 h-48 bg-purple-500/20 rounded-full blur-3xl translate-y-1/2 -translate-x-1/2" />
      
      <div class="relative text-center">
        <h1 class="text-3xl md:text-4xl font-bold bg-gradient-to-r from-white via-white to-indigo-300 bg-clip-text text-transparent">
          Contacto
        </h1>
        <p class="mt-3 text-gray-400 max-w-lg mx-auto">
          ¿Tienes un proyecto en mente? ¡Hablemos!
        </p>
      </div>
    </div>
    
    <!-- Contact Cards -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <!-- Email Card -->
      <a 
        :href="'mailto:' + cv.personalInfo.email"
        class="group relative overflow-hidden bg-gradient-to-br from-indigo-500/20 to-purple-500/20 rounded-2xl border border-indigo-500/30 p-8 hover:border-indigo-500/50 transition-all hover:-translate-y-1"
      >
        <div class="absolute inset-0 bg-gradient-to-br from-indigo-500/10 to-purple-500/10 opacity-0 group-hover:opacity-100 transition-opacity" />
        
        <div class="relative flex flex-col items-center text-center">
          <div class="w-16 h-16 bg-gradient-to-br from-indigo-500 to-purple-500 rounded-2xl flex items-center justify-center mb-4 shadow-lg">
            <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
          </div>
          <h3 class="text-xl font-bold text-white mb-2">Email</h3>
          <p class="text-indigo-300 break-all">{{ cv.personalInfo.email }}</p>
          <p class="mt-2 text-sm text-gray-400">Escríbeme un correo</p>
        </div>
      </a>
      
      <!-- GitHub Card -->
      <a 
        v-if="cv.personalInfo.social?.github"
        :href="cv.personalInfo.social.github"
        target="_blank"
        class="group relative overflow-hidden bg-gradient-to-br from-gray-800/50 to-gray-900/50 rounded-2xl border border-white/10 p-8 hover:border-white/20 transition-all hover:-translate-y-1"
      >
        <div class="absolute inset-0 bg-white/5 opacity-0 group-hover:opacity-100 transition-opacity" />
        
        <div class="relative flex flex-col items-center text-center">
          <div class="w-16 h-16 bg-gradient-to-br from-gray-700 to-gray-800 rounded-2xl flex items-center justify-center mb-4 border border-white/10">
            <svg class="w-8 h-8 text-white" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
              <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd" />
            </svg>
          </div>
          <h3 class="text-xl font-bold text-white mb-2">GitHub</h3>
          <p class="text-gray-400">@aaralvrod</p>
          <p class="mt-2 text-sm text-gray-500">Explora mis proyectos</p>
        </div>
      </a>
    </div>
    
    <!-- Back to Home -->
    <div class="text-center pt-4">
      <router-link 
        to="/" 
        class="inline-flex items-center gap-2 px-6 py-3 border border-white/20 text-white rounded-xl font-medium hover:bg-white/10 transition-all"
      >
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18" />
        </svg>
        Volver al inicio
      </router-link>
    </div>
  </div>
</template>

<script setup lang="ts">
import cv from '../data/cv.json'
</script>

