<template>
  <div class="space-y-8">
    
    <!-- GRID HERO SECTION -->
    <div class="bento-grid grid-rows-[auto]">
      
      <!-- 1. Intro Card (col-span-2) -->
      <div class="col-span-1 md:col-span-2 bento-card p-8 md:p-10 flex flex-col justify-center relative overflow-hidden group border-t border-t-accent-blue/20">
        <div class="absolute -top-24 -right-24 w-80 h-80 bg-accent-blue/10 rounded-full blur-[80px] group-hover:bg-accent-blue/20 transition-all duration-700"></div>
        <div class="relative z-10 space-y-6">
          <div class="flex flex-wrap items-center gap-3">
            <span class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full bg-green-500/10 border border-green-500/20 backdrop-blur-md">
              <span class="w-1.5 h-1.5 rounded-full bg-green-500 animate-pulse"></span>
              <span class="text-[10px] font-bold text-green-400 uppercase tracking-wider">Disponible para trabajar</span>
            </span>
          </div>
          <div>
            <h1 class="text-3xl md:text-5xl font-extrabold text-white tracking-tight leading-none mb-2">
              Hola, soy 
              <span class="text-transparent bg-clip-text bg-gradient-to-r from-accent-blue via-accent-purple to-accent-cyan text-glow">
                {{ cv.personalInfo.name }}
              </span>
            </h1>
            <p class="text-lg md:text-xl text-gray-300 font-medium">
              {{ cv.personalInfo.title }}
            </p>
          </div>
          <p class="text-bento-subtext text-sm md:text-base leading-relaxed">
             {{ cv.personalInfo.extendedBio || cv.personalInfo.bio }}
          </p>
        </div>
      </div>

      <!-- 2. Local Time Widget (col-span-1) -->
      <div class="col-span-1 bento-card p-6 md:p-8 flex flex-col justify-between relative overflow-hidden group border-t border-t-accent-purple/20">
        <!-- SVG Map Background/Radar Pattern -->
        <div class="absolute inset-0 opacity-10 group-hover:opacity-15 transition-opacity duration-700 pointer-events-none">
          <svg class="w-full h-full" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="100" cy="100" r="80" stroke="white" stroke-width="0.5" stroke-dasharray="2 4"/>
            <circle cx="100" cy="100" r="50" stroke="white" stroke-width="0.5"/>
            <line x1="100" y1="20" x2="100" y2="180" stroke="white" stroke-width="0.5"/>
            <line x1="20" y1="100" x2="180" y2="100" stroke="white" stroke-width="0.5"/>
            <circle cx="100" cy="100" r="4" fill="#BF5AF2" class="animate-ping"/>
            <circle cx="100" cy="100" r="3" fill="#BF5AF2"/>
          </svg>
        </div>
        
        <div class="relative z-10 flex justify-between items-start">
          <div class="flex items-center gap-2 text-bento-subtext text-xs font-semibold uppercase tracking-wider">
            <MapPin class="w-4 h-4 text-accent-purple" />
            <span>Tenerife, España</span>
          </div>
          <span class="text-2xl">🏝️</span>
        </div>

        <div class="relative z-10 my-6">
          <div class="text-4xl md:text-5xl font-mono font-bold text-white tracking-widest text-glow select-none">
            {{ formatTime }}
          </div>
          <div class="text-xs text-bento-subtext mt-2 font-medium">
            La Orotava • Hora local (UTC+1)
          </div>
        </div>

        <div class="relative z-10 text-xs text-accent-purple/80 bg-accent-purple/5 border border-accent-purple/10 px-3 py-2 rounded-xl w-fit flex items-center gap-1.5 font-medium">
          <Clock class="w-3.5 h-3.5" />
          <span>GMT / Atlantic Time</span>
        </div>
      </div>

      <!-- 3. Social Map / Connect Widget (col-span-1) -->
      <div class="col-span-1 bento-card p-6 md:p-8 flex flex-col justify-between relative overflow-hidden group border-t border-t-accent-cyan/20">
        <div class="absolute -bottom-24 -left-24 w-60 h-60 bg-accent-cyan/5 rounded-full blur-[60px] pointer-events-none"></div>
        
        <div class="relative z-10 flex justify-between items-start">
          <span class="text-xs font-bold text-bento-subtext uppercase tracking-wider">Contacto y Redes</span>
          <span class="text-xl">👋</span>
        </div>

        <div class="relative z-10 space-y-3 my-6">
          <a 
            :href="cv.personalInfo.social.github" 
            target="_blank" 
            class="flex items-center justify-between p-3 rounded-2xl bg-white/5 border border-white/5 hover:bg-white/10 hover:border-white/10 hover:shadow-lg hover:shadow-white/5 transition-all group/link"
          >
            <div class="flex items-center gap-3">
              <Github class="w-5 h-5 text-gray-300 group-hover/link:text-white transition-colors" />
              <span class="text-sm font-semibold text-gray-300 group-hover/link:text-white transition-colors">GitHub</span>
            </div>
            <ArrowUpRight class="w-4 h-4 text-bento-subtext group-hover/link:text-white transition-all transform group-hover/link:translate-x-0.5 group-hover/link:-translate-y-0.5" />
          </a>

          <a 
            :href="cv.personalInfo.social.linkedin" 
            target="_blank" 
            class="flex items-center justify-between p-3 rounded-2xl bg-white/5 border border-white/5 hover:bg-white/10 hover:border-accent-blue/30 hover:shadow-lg hover:shadow-accent-blue/10 transition-all group/link"
          >
            <div class="flex items-center gap-3">
              <Linkedin class="w-5 h-5 text-gray-300 group-hover/link:text-accent-blue transition-colors" />
              <span class="text-sm font-semibold text-gray-300 group-hover/link:text-white transition-colors">LinkedIn</span>
            </div>
            <ArrowUpRight class="w-4 h-4 text-bento-subtext group-hover/link:text-accent-blue transition-all transform group-hover/link:translate-x-0.5 group-hover/link:-translate-y-0.5" />
          </a>

          <a 
            :href="'mailto:' + cv.personalInfo.email" 
            class="flex items-center justify-between p-3 rounded-2xl bg-white/5 border border-white/5 hover:bg-white/10 hover:border-accent-cyan/30 hover:shadow-lg hover:shadow-accent-cyan/10 transition-all group/link"
          >
            <div class="flex items-center gap-3">
              <Mail class="w-5 h-5 text-gray-300 group-hover/link:text-accent-cyan transition-colors" />
              <span class="text-sm font-semibold text-gray-300 group-hover/link:text-white transition-colors">Correo</span>
            </div>
            <ArrowUpRight class="w-4 h-4 text-bento-subtext group-hover/link:text-accent-cyan transition-all transform group-hover/link:translate-x-0.5 group-hover/link:-translate-y-0.5" />
          </a>
        </div>

        <div class="relative z-10 text-xs text-bento-subtext font-medium">
          Hablemos de nuevos proyectos
        </div>
      </div>

      <!-- 4. Skills Categories (col-span-3) -->
      <div class="col-span-1 md:col-span-3 bento-card p-8 bg-bento-card/80 flex flex-col justify-between border-t border-t-white/5 relative overflow-hidden group">
        <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-96 h-96 bg-white/1 rounded-full blur-[100px] pointer-events-none"></div>
        <div class="relative z-10 space-y-6">
          <div class="flex items-center gap-2">
            <Sparkles class="w-4 h-4 text-accent-blue" />
            <span class="text-xs font-bold text-bento-subtext uppercase tracking-wider">Stack Tecnológico</span>
          </div>
          
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <!-- Frontend -->
            <div class="space-y-4">
               <div class="flex items-center gap-2 mb-2">
                  <div class="p-2 rounded-lg bg-blue-500/10 text-blue-400">
                     <Code2 class="w-4 h-4" />
                  </div>
                  <h3 class="font-bold text-white tracking-wide text-sm">Frontend</h3>
               </div>
               <div class="flex flex-wrap gap-2">
                  <span v-for="skill in cv.skills.frontend" :key="skill" class="px-2.5 py-1.5 bg-white/5 rounded-xl text-xs text-gray-300 border border-white/5 hover:bg-white/10 hover:border-blue-500/30 transition-all cursor-default hover:text-white">
                     {{ skill }}
                  </span>
               </div>
            </div>

            <!-- Backend -->
            <div class="space-y-4 border-t md:border-t-0 md:border-l border-white/5 pt-6 md:pt-0 md:pl-8">
               <div class="flex items-center gap-2 mb-2">
                  <div class="p-2 rounded-lg bg-purple-500/10 text-purple-400">
                     <Server class="w-4 h-4" />
                  </div>
                  <h3 class="font-bold text-white tracking-wide text-sm">Backend</h3>
               </div>
               <div class="flex flex-wrap gap-2">
                  <span v-for="skill in cv.skills.backend" :key="skill" class="px-2.5 py-1.5 bg-white/5 rounded-xl text-xs text-gray-300 border border-white/5 hover:bg-white/10 hover:border-purple-500/30 transition-all cursor-default hover:text-white">
                     {{ skill }}
                  </span>
               </div>
            </div>

            <!-- Tools -->
            <div class="space-y-4 border-t md:border-t-0 md:border-l border-white/5 pt-6 md:pt-0 md:pl-8">
               <div class="flex items-center gap-2 mb-2">
                  <div class="p-2 rounded-lg bg-green-500/10 text-green-400">
                     <Wrench class="w-4 h-4" />
                  </div>
                  <h3 class="font-bold text-white tracking-wide text-sm">Herramientas</h3>
               </div>
               <div class="flex flex-wrap gap-2">
                  <span v-for="skill in cv.skills.tools" :key="skill" class="px-2.5 py-1.5 bg-white/5 rounded-xl text-xs text-gray-300 border border-white/5 hover:bg-white/10 hover:border-green-500/30 transition-all cursor-default hover:text-white">
                     {{ skill }}
                  </span>
               </div>
            </div>
          </div>
        </div>
      </div>

      <!-- 5. Status / Live activity Widget (col-span-1) -->
      <div class="col-span-1 bento-card p-6 md:p-8 flex flex-col justify-between relative overflow-hidden group border-t border-t-white/5">
        <div class="relative z-10 flex justify-between items-start">
          <div class="flex items-center gap-2 text-bento-subtext text-xs font-semibold uppercase tracking-wider">
            <span class="relative flex h-2 w-2">
              <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-accent-blue opacity-75"></span>
              <span class="relative inline-flex rounded-full h-2 w-2 bg-accent-blue"></span>
            </span>
            <span>Actividad</span>
          </div>
          <Layers class="w-4 h-4 text-accent-blue/60" />
        </div>

        <div class="relative z-10 my-6 space-y-2">
          <div class="text-sm font-bold text-white">
            Programando en Vue 3 & Django
          </div>
          <p class="text-xs text-bento-subtext leading-relaxed">
            Actualmente enfocado en construir APIs robustas y dashboards interactivos.
          </p>
        </div>

        <!-- Soundwave simulation animation -->
        <div class="relative z-10 flex items-end gap-1 h-6">
          <span class="w-1 bg-accent-blue/40 rounded-full animate-soundwave" style="animation-delay: 0.1s;"></span>
          <span class="w-1 bg-accent-blue/80 rounded-full animate-soundwave" style="animation-delay: 0.3s;"></span>
          <span class="w-1 bg-accent-blue rounded-full animate-soundwave" style="animation-delay: 0.5s;"></span>
          <span class="w-1 bg-accent-blue/60 rounded-full animate-soundwave" style="animation-delay: 0.2s;"></span>
          <span class="w-1 bg-accent-blue/30 rounded-full animate-soundwave" style="animation-delay: 0.4s;"></span>
        </div>
      </div>

    </div>

    <!-- PROJECTS GRID -->
    <div class="pt-8">
      <div class="flex justify-between items-end mb-6 px-2">
        <div class="flex items-center gap-2">
          <Sparkles class="w-5 h-5 text-accent-blue" />
          <h2 class="text-2xl font-bold text-white">Proyectos Destacados</h2>
        </div>
        <router-link to="/proyectos" class="text-accent-blue text-sm hover:underline flex items-center gap-0.5 group">
          <span>Ver todos</span>
          <ChevronRight class="w-4 h-4 transform group-hover:translate-x-0.5 transition-transform" />
        </router-link>
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
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 pt-8 max-w-7xl mx-auto pb-6">
      
      <!-- EXPERIENCE LIST -->
      <div>
        <div class="flex items-center gap-2 mb-6 px-2">
          <Briefcase class="w-5 h-5 text-accent-blue" />
          <h2 class="text-2xl font-bold text-white">Experiencia Laboral</h2>
        </div>
        
        <div class="space-y-4">
           <div 
              v-for="job in cv.experience" 
              :key="job.id" 
              class="bento-card p-6 flex flex-col gap-4 border border-white/5 hover:border-accent-blue/20 hover:shadow-lg hover:shadow-accent-blue/5 transition-all"
           >
              <div class="flex justify-between items-start">
                 <div class="flex gap-4 items-center">
                    <div class="w-12 h-12 rounded-xl bg-white/5 border border-white/5 flex items-center justify-center text-accent-blue shrink-0">
                       <Briefcase class="w-5 h-5" />
                    </div>
                    <div>
                       <h3 class="font-bold text-white text-base md:text-lg">{{ job.role }}</h3>
                       <p class="text-sm text-bento-subtext font-medium">{{ job.company }}</p>
                    </div>
                 </div>
                 <div class="text-[10px] md:text-xs text-bento-subtext font-mono bg-white/5 px-3 py-1.5 rounded-full border border-white/5 whitespace-nowrap">
                    {{ job.period }}
                 </div>
              </div>
              
              <ul class="text-bento-subtext text-sm md:text-base leading-relaxed space-y-2 list-none">
                 <li 
                    v-for="(item, index) in job.description.split('. ').filter(i => i.trim())" 
                    :key="index"
                    class="flex gap-2"
                 >
                    <span class="text-accent-blue/80 font-bold">•</span>
                    <span>{{ item.trim().endsWith('.') ? item.trim() : item.trim() + '.' }}</span>
                 </li>
              </ul>

              <div class="flex flex-wrap gap-2 mt-2">
                 <span 
                    v-for="tech in job.technologies" 
                    :key="tech"
                    class="px-2.5 py-1 text-xs font-semibold text-accent-blue bg-accent-blue/10 rounded-lg border border-accent-blue/10"
                 >
                    {{ tech }}
                 </span>
              </div>
           </div>
        </div>
      </div>

      <!-- EDUCATION, LANGUAGES & INFO LIST -->
      <div class="h-fit lg:sticky lg:top-24 space-y-8">
        
        <!-- EDUCATION -->
        <div>
          <div class="flex items-center gap-2 mb-6 px-2">
            <GraduationCap class="w-5 h-5 text-accent-purple" />
            <h2 class="text-2xl font-bold text-white">Educación</h2>
          </div>
          
          <div class="space-y-4">
             <div 
                v-for="edu in cv.education" 
                :key="edu.id" 
                class="bento-card p-6 flex flex-col md:flex-row gap-4 items-start md:items-center justify-between border border-white/5 hover:border-accent-purple/20 hover:shadow-lg hover:shadow-accent-purple/5 transition-all"
             >
                <div class="flex gap-4 items-center">
                   <div class="w-12 h-12 rounded-xl bg-white/5 border border-white/5 flex items-center justify-center text-accent-purple shrink-0">
                      <GraduationCap class="w-5 h-5" />
                   </div>
                   <div>
                      <h3 class="font-bold text-white text-base md:text-lg">{{ edu.degree }}</h3>
                      <p class="text-sm text-bento-subtext font-medium">{{ edu.institution }}</p>
                   </div>
                </div>
                <div class="text-[10px] md:text-xs text-bento-subtext font-mono bg-white/5 px-3 py-1.5 rounded-full border border-white/5 whitespace-nowrap self-start md:self-center">
                   {{ edu.year }}
                </div>
             </div>
          </div>
        </div>

        <!-- LANGUAGES -->
        <div v-if="cv.languages && cv.languages.length">
          <div class="flex items-center gap-2 mb-6 px-2">
            <Languages class="w-5 h-5 text-accent-purple" />
            <h2 class="text-2xl font-bold text-white">Idiomas</h2>
          </div>
          
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
             <div 
                v-for="lang in cv.languages" 
                :key="lang.name" 
                class="bento-card p-5 flex items-center justify-between border border-white/5 hover:border-accent-purple/20 hover:shadow-lg hover:shadow-accent-purple/5 transition-all"
             >
                <div class="flex gap-3 items-center">
                   <div class="w-10 h-10 rounded-lg bg-accent-purple/10 flex items-center justify-center text-accent-purple shrink-0">
                      <Languages class="w-5 h-5" />
                   </div>
                   <div>
                      <h3 class="font-bold text-white text-sm md:text-base">{{ lang.name }}</h3>
                   </div>
                </div>
                <span class="text-xs font-bold px-2.5 py-1 bg-accent-purple/20 text-accent-purple border border-accent-purple/20 rounded-full">
                   {{ lang.level }}
                </span>
             </div>
          </div>
        </div>

        <!-- MORE INFO -->
        <div v-if="cv.additionalInfo && cv.additionalInfo.length">
          <div class="flex items-center gap-2 mb-6 px-2">
            <Info class="w-5 h-5 text-accent-cyan" />
            <h2 class="text-2xl font-bold text-white">Más información</h2>
          </div>
          
          <div class="bento-card p-6 border border-white/5 hover:border-accent-cyan/20 hover:shadow-lg hover:shadow-accent-cyan/5 transition-all">
             <div class="flex flex-wrap gap-3">
                <div 
                   v-for="info in cv.additionalInfo" 
                   :key="info" 
                   class="flex items-center gap-2 px-4 py-2 bg-white/5 rounded-xl border border-white/5 text-xs md:text-sm text-gray-300 hover:border-white/10 transition-colors"
                >
                   <span class="w-2 h-2 rounded-full bg-accent-cyan"></span>
                   <span>{{ info }}</span>
                </div>
             </div>
          </div>
        </div>

      </div>

    </div>

  </div>
</template>

<script setup>
import { inject, computed } from 'vue';
import { useTimestamp } from '@vueuse/core';
import ProjectCard from '@/components/ProjectCard.vue';
import { 
  Github, 
  Linkedin, 
  Mail, 
  MapPin, 
  Clock, 
  ArrowUpRight, 
  Code2, 
  Server, 
  Wrench, 
  Sparkles,
  GraduationCap,
  Briefcase,
  Layers,
  ChevronRight,
  Languages,
  Info
} from 'lucide-vue-next';

const cv = inject('cv');

// Tenerife Time Clock (Atlantic/Canary Time Zone)
const time = useTimestamp({ interval: 1000 });
const formatTime = computed(() => {
  return new Intl.DateTimeFormat('es-ES', {
    timeZone: 'Atlantic/Canary',
    hour: '2-digit',
    minute: '2-digit',
    second: '2-digit',
    hour12: false
  }).format(new Date(time.value));
});
</script>
