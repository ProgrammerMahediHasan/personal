<template>
  <footer class="bg-[#0f172a] border-t border-gray-800 py-12">
    <div class="container mx-auto px-6">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="mb-8 md:mb-0">
          <a href="#" class="text-2xl font-bold text-white tracking-wider">
            M<span class="text-blue-500">H</span>A
          </a>
          <p class="text-gray-500 mt-4 max-w-xs">
            Building digital products, brands, and experiences with passion and precision.
          </p>
        </div>

        <div class="flex space-x-6 mb-8 md:mb-0">
          <a v-for="social in socials" :key="social.name" :href="social.link" class="w-10 h-10 bg-[#1e293b] rounded-full flex items-center justify-center text-gray-400 hover:bg-blue-600 hover:text-white transition-all duration-300">
            <component :is="social.icon" class="w-5 h-5" />
          </a>
        </div>

        <div class="text-gray-500 text-sm">
          &copy; {{ new Date().getFullYear() }} Mahedi Hasan Abir. All rights reserved.
        </div>
      </div>
      
      <!-- Back to Top -->
      <button 
        v-show="showBackToTop"
        @click="scrollToTop"
        class="fixed bottom-8 right-8 w-12 h-12 bg-blue-600 text-white rounded-full flex items-center justify-center shadow-lg hover:bg-blue-700 transition-all transform hover:-translate-y-2 z-50"
      >
        <ArrowUp class="w-6 h-6" />
      </button>
    </div>
  </footer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Linkedin, Github, Facebook, Twitter, ArrowUp } from 'lucide-vue-next'

const showBackToTop = ref(false)

const socials = [
  { name: 'LinkedIn', link: '#', icon: Linkedin },
  { name: 'GitHub', link: '#', icon: Github },
  { name: 'Facebook', link: '#', icon: Facebook },
  { name: 'Twitter', link: '#', icon: Twitter }
]

const handleScroll = () => {
  showBackToTop.value = window.scrollY > 500
}

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>
