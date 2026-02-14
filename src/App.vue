<template>
  <div class="bg-[#0f172a] text-[#f8fafc] selection:bg-blue-600/30">
    <PageLoader :is-loading="isLoading" />
    
    <Navbar :is-dark="isDark" @toggle-dark="toggleDark" />
    
    <main>
      <Hero />
      <About />
      <Skills />
      <Services />
      <Portfolio />
      <Experience />
      <Testimonials />
      <Contact />
    </main>

    <Footer />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import PageLoader from './components/layout/PageLoader.vue'
import Navbar from './components/layout/Navbar.vue'
import Footer from './components/layout/Footer.vue'
import Hero from './components/sections/Hero.vue'
import About from './components/sections/About.vue'
import Skills from './components/sections/Skills.vue'
import Services from './components/sections/Services.vue'
import Portfolio from './components/sections/Portfolio.vue'
import Experience from './components/sections/Experience.vue'
import Testimonials from './components/sections/Testimonials.vue'
import Contact from './components/sections/Contact.vue'

const isLoading = ref(true)
const isDark = ref(true)

const toggleDark = () => {
  isDark.value = !isDark.value
  // In a real app, you'd handle document classes here
}

onMounted(() => {
  // Simulate loading time
  setTimeout(() => {
    isLoading.value = false
  }, 1500)
})
</script>

<style>
/* Global styles if needed */
</style>
