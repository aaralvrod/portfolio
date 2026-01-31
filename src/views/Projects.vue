<template>
  <div class="space-y-8">
    <!-- Header -->
    <div class="relative overflow-hidden rounded-[2rem] bg-bento-card border border-white/5 p-10 md:p-14 text-center group">
      <div class="absolute top-0 inset-x-0 h-40 bg-gradient-to-b from-accent-blue/10 to-transparent opacity-50 group-hover:opacity-100 transition-opacity duration-700" />
      
      <div class="relative z-10">
        <h1 class="text-4xl md:text-5xl font-bold text-white tracking-tight mb-4">
          Proyectos
        </h1>
        <p class="text-bento-subtext text-lg max-w-xl mx-auto leading-relaxed">
          Una colección de aplicaciones, experimentos y soluciones que he construido.
        </p>
      </div>
    </div>
    
    <!-- Projects Grid -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <ProjectCard
        v-for="project in cv.projects"
        :key="project.id"
        :card="project"
      />
    </div>
    
    <!-- Back to Home -->
    <div class="text-center pt-8">
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
import ProjectCard from '../components/ProjectCard.vue'
</script>

