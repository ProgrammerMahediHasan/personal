<template>
  <section id="about" class="py-24 bg-[#0f172a]">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold text-white mb-4">About Me</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div class="grid md:grid-cols-2 gap-16 items-center">
        <div class="relative group" data-aos="fade-right">
          <div class="absolute -inset-4 bg-blue-600/20 rounded-2xl blur-xl group-hover:bg-blue-600/30 transition-all duration-500"></div>
          <img 
            src="https://picsum.photos/seed/about/600/600" 
            alt="About Image" 
            class="relative rounded-2xl shadow-2xl grayscale group-hover:grayscale-0 transition-all duration-700 w-full"
          />
          <div class="absolute bottom-6 right-6 bg-blue-600 px-6 py-4 rounded-xl shadow-xl">
            <p class="text-3xl font-bold text-white">5+</p>
            <p class="text-sm text-blue-100 uppercase tracking-wider">Years Experience</p>
          </div>
        </div>

        <div data-aos="fade-left">
          <h3 class="text-2xl font-bold text-white mb-6">Hello! I'm Mahedi Hasan Abir</h3>
          <p class="text-gray-400 text-lg mb-8 leading-relaxed">
            A passionate Full Stack Web Developer based in Bangladesh. I specialize in building high-quality websites and applications that are both beautiful and functional. My goal is to always provide my clients with the best possible service and to help them achieve their business goals.
          </p>
          
          <div class="grid grid-cols-2 gap-y-4 mb-10">
            <div v-for="(info, index) in personalInfo" :key="index" class="flex flex-col">
              <span class="text-gray-500 text-sm uppercase tracking-wider mb-1">{{ info.label }}</span>
              <span class="text-white font-medium">{{ info.value }}</span>
            </div>
          </div>

          <div class="flex items-center space-x-6">
            <a href="#contact" class="px-8 py-3 bg-blue-600 hover:bg-blue-700 text-white font-semibold rounded-lg transition-all shadow-lg shadow-blue-600/20">
              Get in Touch
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const personalInfo = [
  { label: 'Name', value: 'Mahedi Hasan Abir' },
  { label: 'Email', value: 'contact@mahedi.com' },
  { label: 'Phone', value: '+880 1234 567 890' },
  { label: 'Experience', value: '5+ Years' },
  { label: 'Address', value: 'Dhaka, Bangladesh' },
  { label: 'Freelance', value: 'Available' }
]
</script>
