<template>
  <section id="home" class="min-height-screen flex items-center pt-20">
    <div class="container mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
      <div data-aos="fade-right">
        <h4 class="text-blue-500 font-medium mb-4 tracking-widest uppercase">Welcome to my portfolio</h4>
        <h1 class="text-5xl md:text-7xl font-bold mb-6 text-white leading-tight">
          Hi, I'm <span class="text-blue-500">Mahedi Hasan Abir</span>
        </h1>
        <div class="text-2xl md:text-3xl font-medium text-gray-400 mb-8 h-12">
          <span ref="typeTarget"></span>
        </div>
        <p class="text-gray-400 text-lg mb-10 max-w-lg leading-relaxed">
          Full Stack Web Developer specialized in building exceptional digital experiences. 
          I turn complex problems into elegant, user-friendly solutions.
        </p>
        <div class="flex flex-wrap gap-4">
          <a href="#contact" class="px-8 py-4 bg-blue-600 hover:bg-blue-700 text-white font-semibold rounded-lg transition-all transform hover:-translate-y-1 shadow-lg shadow-blue-600/20">
            Hire Me
          </a>
          <a href="#" class="px-8 py-4 border border-gray-700 hover:border-blue-500 text-white font-semibold rounded-lg transition-all hover:bg-blue-500/10">
            Download CV
          </a>
        </div>
        
        <div class="mt-12 flex space-x-6">
          <a v-for="social in socials" :key="social.name" :href="social.link" class="text-gray-400 hover:text-blue-500 transition-colors">
            <component :is="social.icon" class="w-6 h-6" />
          </a>
        </div>
      </div>
      
      <div class="relative flex justify-center" data-aos="fade-left">
        <div class="w-72 h-72 md:w-[450px] md:h-[450px] relative">
          <!-- Animated Background Blobs -->
          <div class="absolute -top-4 -left-4 w-full h-full bg-blue-600/20 rounded-full blur-3xl animate-pulse"></div>
          <div class="absolute -bottom-4 -right-4 w-full h-full bg-purple-600/20 rounded-full blur-3xl animate-pulse delay-700"></div>
          
          <div class="relative w-full h-full rounded-2xl overflow-hidden border-2 border-gray-800 bg-gray-900 shadow-2xl">
            <img 
              src="https://picsum.photos/seed/mahedi/600/800" 
              alt="Mahedi Hasan Abir" 
              class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import Typed from 'typed.js'
import { Linkedin, Github, Facebook, Twitter } from 'lucide-vue-next'

const typeTarget = ref(null)

const socials = [
  { name: 'LinkedIn', link: '#', icon: Linkedin },
  { name: 'GitHub', link: '#', icon: Github },
  { name: 'Facebook', link: '#', icon: Facebook },
  { name: 'Twitter', link: '#', icon: Twitter }
]

onMounted(() => {
  new Typed(typeTarget.value, {
    strings: ['Full Stack Web Developer', 'UI/UX Designer', 'Laravel Specialist', 'Vue.js Enthusiast'],
    typeSpeed: 50,
    backSpeed: 30,
    loop: true,
    backDelay: 2000
  })
})
</script>

<style scoped>
.min-height-screen {
  min-height: calc(100vh - 80px);
}
</style>
