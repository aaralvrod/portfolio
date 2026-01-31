<template>
  <div class="group relative p-4 bg-gradient-to-br from-white/5 to-white/10 rounded-xl border border-white/10 hover:border-indigo-500/50 transition-all duration-300 hover:shadow-lg hover:shadow-indigo-500/10">
    <div class="absolute inset-0 bg-gradient-to-br from-indigo-500/5 to-purple-500/5 rounded-xl opacity-0 group-hover:opacity-100 transition-opacity" />
    
    <div class="relative">
      <div class="flex items-center gap-3 mb-3">
        <span class="text-2xl">{{ getIcon(skill.name) }}</span>
        <h4 class="font-semibold text-white">{{ skill.name }}</h4>
      </div>
      
      <div class="flex flex-wrap gap-2">
        <span 
          v-for="tech in skill.technologies" 
          :key="tech"
          class="text-xs px-2 py-1 bg-indigo-500/20 text-indigo-300 rounded-full border border-indigo-500/30"
        >
          {{ tech }}
        </span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Skill {
  name: string
  technologies: string[]
}

defineProps<{
  skill: Skill
}>()

const getIcon = (name: string): string => {
  const icons: Record<string, string> = {
    'Frontend': '🎨',
    'Backend': '⚙️',
    'Tools': '🛠️',
    'Database': '🗄️',
    'DevOps': '🚀'
  }
  return icons[name] || '💻'
}
</script>
