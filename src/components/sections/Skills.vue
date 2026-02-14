<template>
  <section id="skills" class="py-24 bg-[#1e293b]/50">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold text-white mb-4">My Skills</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-12">
        <div v-for="(category, index) in skillCategories" :key="index" class="bg-[#0f172a] p-8 rounded-2xl border border-gray-800 hover:border-blue-500/50 transition-all duration-300 shadow-xl" data-aos="fade-up" :data-aos-delay="index * 100">
          <h3 class="text-xl font-bold text-white mb-8 flex items-center">
            <component :is="category.icon" class="w-6 h-6 mr-3 text-blue-500" />
            {{ category.title }}
          </h3>
          
          <div class="space-y-6">
            <div v-for="skill in category.skills" :key="skill.name">
              <div class="flex justify-between mb-2">
                <span class="text-gray-300 font-medium">{{ skill.name }}</span>
                <span class="text-blue-500">{{ skill.level }}%</span>
              </div>
              <div class="w-full h-2 bg-gray-800 rounded-full overflow-hidden">
                <div 
                  class="h-full bg-blue-600 rounded-full transition-all duration-1000 ease-out"
                  :style="{ width: isVisible ? skill.level + '%' : '0%' }"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { Layout, Server, Database } from 'lucide-vue-next'

const isVisible = ref(false)

const skillCategories = [
  {
    title: 'Frontend Development',
    icon: Layout,
    skills: [
      { name: 'HTML/CSS/Sass', level: 95 },
      { name: 'JavaScript (ES6+)', level: 90 },
      { name: 'Vue.js / React', level: 85 },
      { name: 'Tailwind CSS', level: 95 }
    ]
  },
  {
    title: 'Backend Development',
    icon: Server,
    skills: [
      { name: 'PHP / Laravel', level: 90 },
      { name: 'Node.js / Express', level: 75 },
      { name: 'Python / Django', level: 70 },
      { name: 'RESTful APIs', level: 85 }
    ]
  },
  {
    title: 'Tools & Database',
    icon: Database,
    skills: [
      { name: 'MySQL / PostgreSQL', level: 85 },
      { name: 'MongoDB', level: 70 },
      { name: 'Git / GitHub', level: 90 },
      { name: 'Docker / AWS', level: 65 }
    ]
  }
]

onMounted(() => {
  // Simple intersection observer to trigger progress bar animation
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      isVisible.value = true
    }
  }, { threshold: 0.1 })
  
  const section = document.querySelector('#skills')
  if (section) observer.observe(section)
})
</script>
