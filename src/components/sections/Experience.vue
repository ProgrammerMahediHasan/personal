<template>
  <section id="experience" class="py-24 bg-[#0f172a]">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold text-white mb-4">Experience & Education</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div class="max-w-4xl mx-auto">
        <div class="relative">
          <!-- Vertical Line -->
          <div class="absolute left-0 md:left-1/2 transform md:-translate-x-1/2 w-0.5 h-full bg-gray-800"></div>

          <!-- Timeline Items -->
          <div v-for="(item, index) in timeline" :key="index" class="mb-12 relative flex flex-col md:flex-row items-center">
            <!-- Dot -->
            <div class="absolute left-0 md:left-1/2 transform -translate-x-1/2 w-4 h-4 rounded-full bg-blue-600 border-4 border-[#0f172a] z-10"></div>

            <!-- Content -->
            <div 
              :class="[
                'w-full md:w-1/2 pl-8 md:pl-0',
                index % 2 === 0 ? 'md:pr-12 md:text-right' : 'md:ml-auto md:pl-12'
              ]"
              data-aos="fade-up"
              :data-aos-delay="index * 100"
            >
              <div class="bg-[#1e293b]/50 p-6 rounded-2xl border border-gray-800 hover:border-blue-500/30 transition-all duration-300">
                <span class="text-blue-500 font-bold text-sm uppercase tracking-widest mb-2 block">{{ item.date }}</span>
                <h3 class="text-xl font-bold text-white mb-1">{{ item.title }}</h3>
                <h4 class="text-gray-400 font-medium mb-4">{{ item.company }}</h4>
                <p class="text-gray-500 text-sm leading-relaxed">{{ item.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const timeline = [
  {
    date: '2022 - Present',
    title: 'Senior Web Developer',
    company: 'Tech Solutions Ltd.',
    description: 'Lead developer for major e-commerce platforms. Improved site performance by 40% and mentored junior developers.'
  },
  {
    date: '2020 - 2022',
    title: 'Full Stack Developer',
    company: 'Creative Agency',
    description: 'Developed custom WordPress themes and Laravel applications for diverse international clients.'
  },
  {
    date: '2018 - 2020',
    title: 'Junior Web Developer',
    company: 'Startup Hub',
    description: 'Maintained and updated existing codebases. Collaborated with UI/UX designers to implement responsive layouts.'
  },
  {
    date: '2014 - 2018',
    title: 'B.Sc. in Computer Science',
    company: 'University of Engineering & Technology',
    description: 'Focused on software engineering, algorithms, and web technologies. Graduated with honors.'
  }
]
</script>
