<template>
  <section id="portfolio" class="py-24 bg-[#1e293b]/50">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold text-white mb-4">Portfolio</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <!-- Filter Tabs -->
      <div class="flex flex-wrap justify-center gap-4 mb-12" data-aos="fade-up">
        <button 
          v-for="tab in tabs" 
          :key="tab"
          @click="activeTab = tab"
          :class="[
            'px-6 py-2 rounded-full font-medium transition-all duration-300',
            activeTab === tab 
              ? 'bg-blue-600 text-white shadow-lg shadow-blue-600/20' 
              : 'text-gray-400 hover:text-white border border-gray-800 hover:border-blue-500/50'
          ]"
        >
          {{ tab }}
        </button>
      </div>

      <!-- Projects Grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(project, index) in filteredProjects" 
          :key="index"
          class="group relative overflow-hidden rounded-2xl bg-[#0f172a] border border-gray-800 hover:border-blue-500/50 transition-all duration-500 shadow-xl"
          data-aos="fade-up"
          :data-aos-delay="index * 100"
        >
          <!-- Project Image -->
          <div class="aspect-video overflow-hidden">
            <img 
              :src="project.image" 
              :alt="project.title" 
              class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700 grayscale group-hover:grayscale-0"
            />
          </div>

          <!-- Overlay -->
          <div class="absolute inset-0 bg-gradient-to-t from-[#0f172a] via-[#0f172a]/80 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col justify-end p-8">
            <span class="text-blue-500 text-sm font-medium mb-2 uppercase tracking-widest">{{ project.category }}</span>
            <h3 class="text-2xl font-bold text-white mb-3">{{ project.title }}</h3>
            <p class="text-gray-300 text-sm mb-6 line-clamp-2">{{ project.description }}</p>
            
            <div class="flex space-x-4">
              <a :href="project.liveLink" class="p-3 bg-blue-600 rounded-full text-white hover:bg-blue-700 transition-colors shadow-lg">
                <ExternalLink class="w-5 h-5" />
              </a>
              <a :href="project.githubLink" class="p-3 bg-gray-800 rounded-full text-white hover:bg-gray-700 transition-colors shadow-lg">
                <Github class="w-5 h-5" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import { ExternalLink, Github } from 'lucide-vue-next'

const tabs = ['All', 'Web Apps', 'UI Design', 'Full Stack']
const activeTab = ref('All')

const projects = [
  {
    title: 'E-commerce Dashboard',
    category: 'Full Stack',
    image: 'https://picsum.photos/seed/project1/800/600',
    description: 'A comprehensive admin dashboard built with Laravel and Vue 3.',
    liveLink: '#',
    githubLink: '#'
  },
  {
    title: 'Modern Portfolio Template',
    category: 'UI Design',
    image: 'https://picsum.photos/seed/project2/800/600',
    description: 'A sleek, minimalist portfolio design for creative professionals.',
    liveLink: '#',
    githubLink: '#'
  },
  {
    title: 'Real-time Chat App',
    category: 'Web Apps',
    image: 'https://picsum.photos/seed/project3/800/600',
    description: 'Real-time messaging application using Node.js and Socket.io.',
    liveLink: '#',
    githubLink: '#'
  },
  {
    title: 'Fintech Mobile UI',
    category: 'UI Design',
    image: 'https://picsum.photos/seed/project4/800/600',
    description: 'Mobile banking app interface with dark mode support.',
    liveLink: '#',
    githubLink: '#'
  },
  {
    title: 'SaaS Landing Page',
    category: 'Web Apps',
    image: 'https://picsum.photos/seed/project5/800/600',
    description: 'Conversion-focused landing page with smooth animations.',
    liveLink: '#',
    githubLink: '#'
  },
  {
    title: 'Social Media API',
    category: 'Full Stack',
    image: 'https://picsum.photos/seed/project6/800/600',
    description: 'Robust RESTful API for a social networking platform.',
    liveLink: '#',
    githubLink: '#'
  }
]

const filteredProjects = computed(() => {
  if (activeTab.value === 'All') return projects
  return projects.filter(project => project.category === activeTab.value)
})
</script>
