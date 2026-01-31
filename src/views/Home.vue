<template>
  <div class="space-y-6">
    
    <!-- GRID HERO SECTION -->
    <div class="bento-grid grid-rows-[auto] md:grid-rows-[minmax(300px,auto)_auto]">
      
      <!-- 1. Intro Card (Large - Expanded) -->
      <div class="col-span-1 md:col-span-3 row-span-1 bento-card p-10 flex flex-col justify-center relative overflow-hidden group border-l-4 border-l-accent-blue/50">
        <div class="absolute top-0 right-0 w-80 h-80 bg-accent-blue/10 rounded-full blur-[80px] group-hover:bg-accent-blue/20 transition-all duration-700"></div>
        <div class="relative z-10">
          <h1 class="text-3xl md:text-5xl font-bold text-white mb-6 tracking-tight leading-[1.1]">
            <div class="flex flex-wrap items-center gap-3">
              <span class="text-transparent bg-clip-text bg-gradient-to-r from-accent-blue to-accent-cyan text-glow">
                {{ cv.personalInfo.name }}
              </span>
              <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-green-500/10 border border-green-500/20 backdrop-blur-md">
                <span class="w-2 h-2 rounded-full bg-green-500 animate-pulse"></span>
                <span class="text-xs font-bold text-green-400 uppercase tracking-wider">Open to Work</span>
              </span>
            </div>
            <span class="block text-xl md:text-2xl text-white mt-2 font-normal">
              {{ cv.personalInfo.title }}
            </span>
          </h1>
          <p class="text-bento-subtext max-w-2xl mb-6 text-base md:text-lg font-medium leading-relaxed">
             {{ cv.personalInfo.extendedBio || cv.personalInfo.bio }}
          </p>

        </div>
      </div>

      <!-- 3. Social Map / Contact -->
      <div class="col-span-1 md:col-span-1 bento-card bg-[#007AFF] p-6 text-white flex flex-col justify-between hover:bg-[#0066CC]">
         <div class="flex justify-between items-start">
            <span class="text-3xl">👋</span>
            <div class="flex gap-2">
               <a href="https://github.com/aaralvrod" target="_blank" class="p-2 bg-white/20 rounded-full hover:bg-white/40 transition-colors">
                  <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
               </a>
               <a href="https://linkedin.com/in/aaralvrod" target="_blank" class="p-2 bg-white/20 rounded-full hover:bg-white/40 transition-colors">
                  <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
               </a>
            </div>
         </div>
         <div>
            <p class="font-bold text-xl mb-1">Let's Connect</p>
            <p class="text-white/80 text-sm">Follow my journey</p>
         </div>
      </div>

      <!-- 4. Skills Categories (Span 4) -->
      <div class="col-span-1 md:col-span-4 bento-card p-8 bg-bento-card/80">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          
          <!-- Frontend -->
          <div class="space-y-4">
             <div class="flex items-center gap-2 mb-2">
                <span class="p-2 rounded-lg bg-blue-500/10 text-blue-400">
                   <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" /></svg>
                </span>
                <h3 class="font-bold text-white tracking-wide">Frontend</h3>
             </div>
             <div class="flex flex-wrap gap-2">
                <span v-for="skill in cv.skills.frontend" :key="skill" class="px-3 py-1.5 bg-white/5 rounded-md text-sm text-gray-300 border border-white/5 hover:bg-white/10 hover:border-blue-500/30 transition-all cursor-default">
                   {{ skill }}
                </span>
             </div>
          </div>

          <!-- Backend -->
          <div class="space-y-4 border-t md:border-t-0 md:border-l border-white/5 pt-6 md:pt-0 md:pl-8">
             <div class="flex items-center gap-2 mb-2">
                <span class="p-2 rounded-lg bg-purple-500/10 text-purple-400">
                   <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01" /></svg>
                </span>
                <h3 class="font-bold text-white tracking-wide">Backend</h3>
             </div>
             <div class="flex flex-wrap gap-2">
                <span v-for="skill in cv.skills.backend" :key="skill" class="px-3 py-1.5 bg-white/5 rounded-md text-sm text-gray-300 border border-white/5 hover:bg-white/10 hover:border-purple-500/30 transition-all cursor-default">
                   {{ skill }}
                </span>
             </div>
          </div>

          <!-- Tools -->
          <div class="space-y-4 border-t md:border-t-0 md:border-l border-white/5 pt-6 md:pt-0 md:pl-8">
             <div class="flex items-center gap-2 mb-2">
                <span class="p-2 rounded-lg bg-green-500/10 text-green-400">
                   <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" /><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" /></svg>
                </span>
                <h3 class="font-bold text-white tracking-wide">Tools</h3>
             </div>
             <div class="flex flex-wrap gap-2">
                <span v-for="skill in cv.skills.tools" :key="skill" class="px-3 py-1.5 bg-white/5 rounded-md text-sm text-gray-300 border border-white/5 hover:bg-white/10 hover:border-green-500/30 transition-all cursor-default">
                   {{ skill }}
                </span>
             </div>
          </div>

        </div>
      </div>

    </div>

    <!-- PROJECTS GRID -->
    <div class="pt-10">
      <div class="flex justify-between items-end mb-6 px-2">
        <h2 class="text-2xl font-bold text-white">Selected Projects</h2>
        <router-link to="/proyectos" class="text-apple-blue text-sm hover:underline">View All</router-link>
      </div>
      
      <div class="bento-grid">
         <ProjectCard 
            v-for="project in cv.projects.filter(p => p.featured).slice(0, 6)" 
            :key="project.id" 
            :card="project" 
            class="md:col-span-2 h-[300px]"
         />
      </div>
    </div>

    <!-- EXPERIENCE & EDUCATION GRID -->
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 pt-10 max-w-7xl mx-auto pb-10">
      
      <!-- EXPERIENCE LIST -->
      <div>
        <h2 class="text-2xl font-bold text-white mb-6 px-2">Experience</h2>
        <div class="space-y-4">
           <div 
              v-for="job in cv.experience" 
              :key="job.id" 
              class="bento-card p-6 flex flex-col gap-4"
           >
              <div class="flex justify-between items-start">
                 <div class="flex gap-4 items-center">
                    <div class="w-12 h-12 rounded-xl bg-white/10 flex items-center justify-center text-xl shrink-0">
                       💼
                    </div>
                    <div>
                       <h3 class="font-bold text-white text-lg">{{ job.role }}</h3>
                       <p class="text-sm text-bento-subtext">{{ job.company }}</p>
                    </div>
                 </div>
                 <div class="text-xs text-bento-subtext font-mono bg-white/5 px-3 py-1.5 rounded-full border border-white/5 whitespace-nowrap">
                    {{ job.period }}
                 </div>
              </div>
              
              <ul class="text-bento-subtext text-base leading-relaxed space-y-2 list-none">
                 <li 
                    v-for="(item, index) in job.description.split('. ').filter(i => i.trim())" 
                    :key="index"
                    class="flex gap-2"
                 >
                    <span class="text-accent-blue/60">-</span>
                    <span>{{ item.trim().endsWith('.') ? item.trim() : item.trim() + '.' }}</span>
                 </li>
              </ul>

              <div class="flex flex-wrap gap-2 mt-2">
                 <span 
                    v-for="tech in job.technologies" 
                    :key="tech"
                    class="px-2.5 py-1 text-xs font-medium text-accent-blue bg-accent-blue/10 rounded-md border border-accent-blue/10"
                 >
                    {{ tech }}
                 </span>
              </div>
           </div>
        </div>
      </div>

      <!-- EDUCATION LIST -->
      <div class="h-fit lg:sticky lg:top-24">
        <h2 class="text-2xl font-bold text-white mb-6 px-2">Education</h2>
        <div class="space-y-4">
           <div 
              v-for="edu in cv.education" 
              :key="edu.id" 
              class="bento-card p-6 flex flex-col md:flex-row gap-4 items-start md:items-center justify-between"
           >
              <div class="flex gap-4 items-center">
                 <div class="w-12 h-12 rounded-xl bg-white/10 flex items-center justify-center text-xl shrink-0">
                    🎓
                 </div>
                 <div>
                    <h3 class="font-bold text-white text-lg">{{ edu.degree }}</h3>
                    <p class="text-sm text-bento-subtext">{{ edu.institution }}</p>
                 </div>
              </div>
              <div class="text-xs text-bento-subtext font-mono bg-white/5 px-3 py-1.5 rounded-full border border-white/5 whitespace-nowrap self-start md:self-center">
                 {{ edu.year }}
              </div>
           </div>
        </div>
      </div>

    </div>

  </div>
</template>

<script setup>
import { inject } from 'vue';
import ProjectCard from '@/components/ProjectCard.vue';

const cv = inject('cv');
</script>
