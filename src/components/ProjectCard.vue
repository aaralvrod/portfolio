<template>
  <div class="bento-card group flex flex-col h-full bg-bento-card relative overflow-hidden transition-all hover:-translate-y-1">
    
    <!-- Preview / Image Area -->
    <div class="h-52 bg-gradient-to-br from-neutral-800 to-black relative overflow-hidden group-hover:brightness-110 transition-all border-b border-white/5">
      <!-- Grid Pattern Background -->
      <div class="absolute inset-0 opacity-20" style="background-image: radial-gradient(#ffffff 1px, transparent 1px); background-size: 20px 20px;"></div>
      
      <!-- Abstract App Icon / Logo Placeholder -->
      <div class="absolute inset-0 flex items-center justify-center">
         <div class="w-16 h-16 rounded-2xl bg-gradient-to-tr from-gray-700 to-gray-600 shadow-2xl flex items-center justify-center border border-white/10 group-hover:scale-110 transition-transform duration-500">
            <span class="text-2xl font-bold text-white">{{ card.title.charAt(0) }}</span>
         </div>
      </div>

      <!-- Featured Badge -->
      <div v-if="card.featured" class="absolute top-4 right-4 px-3 py-1 bg-accent-blue/20 backdrop-blur-md rounded-full border border-accent-blue/20 text-[10px] font-bold text-accent-blue uppercase tracking-wider">
        Featured
      </div>
    </div>

    <!-- Content Area -->
    <div class="p-6 flex-1 flex flex-col">
      <div class="mb-4">
        <h3 class="font-bold text-xl text-white mb-2 group-hover:text-accent-blue transition-colors">{{ card.title }}</h3>
        <p class="text-bento-subtext text-sm leading-relaxed line-clamp-3">
          {{ card.description }}
        </p>
      </div>

      <!-- Footer: Tags & Actions -->
      <div class="mt-auto pt-4 border-t border-white/5 flex flex-col gap-4">
        <!-- Tags -->
        <div class="flex flex-wrap gap-2">
          <span 
            v-for="tag in card.tags" 
            :key="tag"
            class="text-[10px] uppercase font-medium px-2 py-1 rounded bg-white/5 text-gray-400"
          >
            {{ tag }}
          </span>
        </div>

        <!-- Buttons -->
        <div class="flex items-center gap-3 mt-2">
          <a 
            v-if="card.demoUrl" 
            :href="card.demoUrl" 
            target="_blank"
            class="flex-1 inline-flex items-center justify-center gap-2 px-4 py-2 bg-white text-black text-sm font-bold rounded-xl hover:bg-gray-200 transition-colors"
          >
            <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" /><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" /></svg>
            Demo
          </a>
          <a 
            v-if="card.codeUrl" 
            :href="card.codeUrl" 
            target="_blank"
            class="flex-1 inline-flex items-center justify-center gap-2 px-4 py-2 bg-white/10 text-white text-sm font-medium rounded-xl border border-white/10 hover:bg-white/20 transition-colors"
          >
            <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" /></svg>
            Code
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  card: {
    type: Object,
    required: true
  }
})
</script>
