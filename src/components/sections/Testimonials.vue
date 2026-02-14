<template>
  <section id="testimonials" class="py-24 bg-[#1e293b]/50 overflow-hidden">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold text-white mb-4">Client Feedback</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div data-aos="fade-up">
        <swiper
          :modules="modules"
          :slides-per-view="1"
          :space-between="30"
          :pagination="{ clickable: true }"
          :autoplay="{ delay: 5000, disableOnInteraction: false }"
          :breakpoints="{
            '768': {
              slidesPerView: 2,
            },
            '1024': {
              slidesPerView: 3,
            }
          }"
          class="pb-16"
        >
          <swiper-slide v-for="(testimonial, index) in testimonials" :key="index">
            <div class="bg-[#0f172a] p-8 rounded-2xl border border-gray-800 relative shadow-xl h-full flex flex-col">
              <Quote class="absolute top-6 right-6 w-10 h-10 text-blue-600/20" />
              
              <div class="flex items-center mb-6">
                <img :src="testimonial.image" :alt="testimonial.name" class="w-16 h-16 rounded-full border-2 border-blue-600/50 object-cover mr-4" />
                <div>
                  <h4 class="text-white font-bold">{{ testimonial.name }}</h4>
                  <p class="text-gray-500 text-sm">{{ testimonial.role }}</p>
                </div>
              </div>

              <div class="flex mb-4">
                <Star v-for="i in 5" :key="i" class="w-4 h-4 text-yellow-500 fill-yellow-500" />
              </div>

              <p class="text-gray-400 italic leading-relaxed flex-grow">
                "{{ testimonial.feedback }}"
              </p>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination, Autoplay } from 'swiper/modules'
import { Quote, Star } from 'lucide-vue-next'

// Swiper styles
import 'swiper/css'
import 'swiper/css/pagination'

const modules = [Pagination, Autoplay]

const testimonials = [
  {
    name: 'John Doe',
    role: 'CEO, TechFlow',
    image: 'https://i.pravatar.cc/150?u=1',
    feedback: 'Mahedi is an exceptional developer. He delivered our project ahead of schedule and the quality of code was top-notch.',
    rating: 5
  },
  {
    name: 'Sarah Smith',
    role: 'Marketing Manager, Brandify',
    image: 'https://i.pravatar.cc/150?u=2',
    feedback: 'The attention to detail and design sense Mahedi brings is incredible. Our website traffic has doubled since the redesign.',
    rating: 5
  },
  {
    name: 'Robert Wilson',
    role: 'Founder, Startuply',
    image: 'https://i.pravatar.cc/150?u=3',
    feedback: 'Work with Mahedi was a breeze. He understood our requirements perfectly and implemented complex features with ease.',
    rating: 5
  },
  {
    name: 'Emily Davis',
    role: 'Product Owner, AppNation',
    image: 'https://i.pravatar.cc/150?u=4',
    feedback: 'His technical expertise in Laravel and Vue.js is impressive. A true professional who cares about the final product.',
    rating: 5
  }
]
</script>

<style>
.swiper-pagination-bullet {
  background: #4b5563 !important;
  opacity: 1 !important;
}
.swiper-pagination-bullet-active {
  background: #2563eb !important;
  width: 24px !important;
  border-radius: 4px !important;
}
</style>
