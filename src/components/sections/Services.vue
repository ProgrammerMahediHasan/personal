<template>
  <section id="services" class="py-24 bg-[#0f172a]">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold text-white mb-4">My Services</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div 
          v-for="(service, index) in services" 
          :key="index" 
          class="group p-8 bg-[#1e293b]/30 rounded-2xl border border-gray-800 hover:border-blue-500/50 hover:bg-[#1e293b]/50 transition-all duration-500 transform hover:-translate-y-2 shadow-xl"
          data-aos="fade-up" 
          :data-aos-delay="index * 100"
        >
          <div class="w-16 h-16 bg-blue-600/10 rounded-xl flex items-center justify-center mb-6 group-hover:bg-blue-600 transition-all duration-500">
            <component :is="service.icon" class="w-8 h-8 text-blue-500 group-hover:text-white transition-all duration-500" />
          </div>
          <h3 class="text-xl font-bold text-white mb-4">{{ service.title }}</h3>
          <p class="text-gray-400 leading-relaxed mb-6">
            {{ service.description }}
          </p>
          <a href="#" class="text-blue-500 font-medium flex items-center group-hover:translate-x-2 transition-transform">
            Learn More <ArrowRight class="w-4 h-4 ml-2" />
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Code2, Palette, Database, Search, ArrowRight, Globe, Smartphone, ShieldCheck } from 'lucide-vue-next'

const services = [
  {
    title: 'Web Development',
    description: 'Custom websites built with the latest technologies. Fast, secure, and SEO-friendly.',
    icon: Code2
  },
  {
    title: 'UI/UX Design',
    description: 'Modern and intuitive designs focused on user experience and brand identity.',
    icon: Palette
  },
  {
    title: 'API Development',
    description: 'Scalable and robust RESTful APIs for your web or mobile applications.',
    icon: Database
  },
  {
    title: 'SEO Optimization',
    description: 'Improve your search engine rankings and increase organic traffic.',
    icon: Search
  },
  {
    title: 'E-commerce',
    description: 'Full-featured online stores with secure payment integration and management.',
    icon: Globe
  },
  {
    title: 'App Design',
    description: 'Mobile-first designs that work seamlessly across all devices and platforms.',
    icon: Smartphone
  },
  {
    title: 'Cloud Services',
    description: 'Deployment and management of applications on AWS, DigitalOcean, or Vercel.',
    icon: ShieldCheck
  },
  {
    title: 'Maintenance',
    description: 'Ongoing support and updates to keep your website running smoothly and securely.',
    icon: Code2
  }
]
</script>
