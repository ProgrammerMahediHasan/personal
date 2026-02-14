<template>
  <nav 
    :class="[
      'fixed w-full z-50 transition-all duration-300',
      isScrolled ? 'bg-[#0f172a]/90 backdrop-blur-md py-4 shadow-lg' : 'bg-transparent py-6'
    ]"
  >
    <div class="container mx-auto px-6 flex justify-between items-center">
      <a href="#" class="text-2xl font-bold text-white tracking-wider">
        M<span class="text-blue-500">H</span>A
      </a>

      <!-- Desktop Menu -->
      <div class="hidden md:flex space-x-8 items-center">
        <a v-for="item in navItems" :key="item.name" :href="item.href" class="text-sm font-medium text-gray-300 hover:text-blue-500 transition-colors">
          {{ item.name }}
        </a>
        <button @click="$emit('toggle-dark')" class="p-2 rounded-full hover:bg-gray-800 transition-colors">
          <component :is="isDark ? 'SunIcon' : 'MoonIcon'" class="w-5 h-5 text-gray-300" />
        </button>
      </div>

      <!-- Mobile Menu Button -->
      <button @click="isMobileMenuOpen = !isMobileMenuOpen" class="md:hidden text-gray-300">
        <MenuIcon v-if="!isMobileMenuOpen" class="w-6 h-6" />
        <XIcon v-else class="w-6 h-6" />
      </button>
    </div>

    <!-- Mobile Menu -->
    <div 
      v-if="isMobileMenuOpen" 
      class="md:hidden bg-[#1e293b] absolute top-full left-0 w-full py-6 px-6 border-t border-gray-800"
    >
      <div class="flex flex-col space-y-4">
        <a 
          v-for="item in navItems" 
          :key="item.name" 
          :href="item.href" 
          @click="isMobileMenuOpen = false"
          class="text-lg font-medium text-gray-300 hover:text-blue-500 transition-colors"
        >
          {{ item.name }}
        </a>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Menu as MenuIcon, X as XIcon, Sun as SunIcon, Moon as MoonIcon } from 'lucide-vue-next'

const props = defineProps({
  isDark: Boolean
})

defineEmits(['toggle-dark'])

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const navItems = [
  { name: 'Home', href: '#' },
  { name: 'About', href: '#about' },
  { name: 'Services', href: '#services' },
  { name: 'Portfolio', href: '#portfolio' },
  { name: 'Experience', href: '#experience' },
  { name: 'Contact', href: '#contact' },
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>
