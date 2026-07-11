<template>
  <div class="bento-card group flex flex-col h-full bg-bento-card relative overflow-hidden transition-all duration-500 hover:-translate-y-1.5 border border-white/5 hover:border-white/10 hover:shadow-2xl hover:shadow-accent-blue/5">
    
    <!-- Preview / Image Area -->
    <div :class="['h-48 relative overflow-hidden group-hover:brightness-110 transition-all border-b border-white/5 bg-gradient-to-br', getGradient(card.id)]">
      <!-- Grid Pattern Background -->
      <div class="absolute inset-0 opacity-15" style="background-image: radial-gradient(#ffffff 1px, transparent 1px); background-size: 20px 20px;"></div>
      
      <!-- Abstract App Icon / Logo -->
      <div class="absolute inset-0 flex items-center justify-center">
         <div :class="['w-14 h-14 rounded-2xl shadow-2xl flex items-center justify-center border group-hover:scale-110 transition-transform duration-500 backdrop-blur-md', getIconClass(card.id)]">
            <FolderGit2 v-if="!card.demoUrl" class="w-6 h-6" />
            <Globe v-else class="w-6 h-6" />
         </div>
      </div>

      <!-- Featured Badge -->
      <div v-if="card.featured" class="absolute top-4 right-4 px-3 py-1 bg-accent-blue/10 backdrop-blur-md rounded-full border border-accent-blue/20 text-[9px] font-bold text-accent-blue uppercase tracking-widest">
        Destacado
      </div>
    </div>

    <!-- Content Area -->
    <div class="p-6 flex-1 flex flex-col">
      <div class="mb-4">
        <h3 class="font-extrabold text-lg text-white mb-2 group-hover:text-accent-blue transition-colors flex items-center gap-1.5">
          <span>{{ card.title }}</span>
        </h3>
        <p class="text-bento-subtext text-xs md:text-sm leading-relaxed line-clamp-3">
          {{ card.description }}
        </p>
      </div>

      <!-- Footer: Tags & Actions -->
      <div class="mt-auto pt-4 border-t border-white/5 flex flex-col gap-4">
        <!-- Tags -->
        <div class="flex flex-wrap gap-1.5">
          <span 
            v-for="tag in card.tags" 
            :key="tag"
            class="text-[9px] font-semibold px-2 py-1 rounded-lg bg-white/5 text-gray-300 border border-white/5"
          >
            {{ tag }}
          </span>
        </div>

        <!-- Buttons -->
        <div class="flex items-center gap-2.5 mt-1">
          <a 
            v-if="card.demoUrl" 
            :href="card.demoUrl" 
            target="_blank"
            class="flex-1 inline-flex items-center justify-center gap-1.5 px-3 py-2 bg-white text-black text-xs font-bold rounded-xl hover:bg-gray-200 transition-colors shadow-lg"
          >
            <ExternalLink class="w-3.5 h-3.5" />
            Demo
          </a>
          <a 
            v-if="card.codeUrl" 
            :href="card.codeUrl" 
            target="_blank"
            class="flex-1 inline-flex items-center justify-center gap-1.5 px-3 py-2 bg-white/5 text-white text-xs font-semibold rounded-xl border border-white/5 hover:bg-white/10 transition-colors"
          >
            <Github class="w-3.5 h-3.5 text-gray-300" />
            Código
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { FolderGit2, Globe, ExternalLink, Github } from 'lucide-vue-next';

defineProps({
  card: {
    type: Object,
    required: true
  }
});

const gradients = [
  'from-blue-600/10 via-indigo-900/30 to-black',
  'from-purple-600/10 via-pink-900/30 to-black',
  'from-emerald-600/10 via-teal-900/30 to-black',
  'from-amber-600/10 via-orange-900/30 to-black',
  'from-rose-600/10 via-red-900/30 to-black',
];

const getGradient = (id) => {
  return gradients[id % gradients.length];
};

const iconColors = [
  'bg-blue-500/10 text-blue-400 border-blue-500/20',
  'bg-purple-500/10 text-purple-400 border-purple-500/20',
  'bg-emerald-500/10 text-emerald-400 border-emerald-500/20',
  'bg-amber-500/10 text-amber-400 border-amber-500/20',
  'bg-rose-500/10 text-rose-400 border-rose-500/20',
];

const getIconClass = (id) => {
  return iconColors[id % iconColors.length];
};
</script>
