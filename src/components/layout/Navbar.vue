<template>
  <nav 
    :class="[
      'fixed w-full z-50 transition-all duration-300',
      isScrolled ? 'bg-[#0f172a]/90 backdrop-blur-md py-4 shadow-lg' : 'bg-transparent py-6'
    ]"
  >
    <div class="container mx-auto px-6 flex justify-between items-center">
      <a
        href="#"
        :class="[
          'text-2xl font-bold tracking-wider',
          isDark ? 'text-white' : 'text-black'
        ]"
      >
        DEVELOPER <span class="text-blue-500">MAHEDI</span>
      </a>

      <div class="hidden md:flex space-x-8 items-center">
        <a
          v-for="item in navItems"
          :key="item.name"
          :href="item.href"
          :class="[
            'text-sm font-medium transition-colors',
            isDark ? 'text-gray-300 hover:text-blue-500' : 'text-black hover:text-blue-600'
          ]"
        >
          {{ item.name }}
        </a>
        <button
          @click="$emit('toggle-dark')"
          class="flex items-center gap-2 pl-2 pr-3 py-1 rounded-full border text-xs font-medium transition-all duration-300 focus:outline-none focus:ring-2 focus:ring-blue-500/60"
          :class="isDark ? 'bg-[#020617]/90 border-gray-700 hover:border-blue-500/70' : 'bg-white/90 border-gray-200 hover:border-blue-500/70'"
        >
          <span
            class="flex items-center justify-center w-6 h-6 rounded-full transition-colors duration-300"
            :class="isDark ? 'bg-yellow-400/10 text-yellow-300' : 'bg-blue-600/10 text-blue-600'"
          >
            <component
              :is="isDark ? SunIcon : MoonIcon"
              class="w-3.5 h-3.5"
            />
          </span>
          <span
            class="uppercase tracking-wide transition-colors duration-300"
            :class="isDark ? 'text-gray-300' : 'text-gray-700'"
          >
            {{ isDark ? 'Dark' : 'Light' }}
          </span>
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
          :class="[
            'text-lg font-medium transition-colors',
            isDark ? 'text-gray-300 hover:text-blue-500' : 'text-black hover:text-blue-600'
          ]"
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
  { name: 'Projects', href: '#portfolio' },
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
