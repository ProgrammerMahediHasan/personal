<template>
  <section id="contact" class="py-24 bg-[#0f172a]">
    <div class="container mx-auto px-6">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-4xl font-bold text-white mb-4">Get In Touch</h2>
        <div class="w-20 h-1 bg-blue-600 mx-auto rounded-full"></div>
      </div>

      <div class="grid lg:grid-cols-3 gap-12">
        <!-- Contact Info -->
        <div class="space-y-8" data-aos="fade-right">
          <div v-for="(info, index) in contactInfo" :key="index" class="flex items-start group">
            <div class="w-12 h-12 bg-[#1e293b] rounded-xl flex items-center justify-center mr-4 group-hover:bg-blue-600 transition-colors duration-300">
              <component :is="info.icon" class="w-6 h-6 text-blue-500 group-hover:text-white transition-colors" />
            </div>
            <div>
              <h4 class="text-white font-bold mb-1">{{ info.label }}</h4>
              <p class="text-gray-400 text-sm leading-relaxed">{{ info.value }}</p>
            </div>
          </div>

          <!-- Map Embed -->
          <div class="rounded-2xl overflow-hidden h-64 border border-gray-800 mt-12 grayscale hover:grayscale-0 transition-all duration-500">
            <iframe 
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d233668.3870369269!2d90.27923991057244!3d23.780573258035957!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3755b8b087026b81%3A0x8fa5690c31864291!2sDhaka!5e0!3m2!1sen!2sbd!4v1625478335431!5m2!1sen!2sbd" 
              width="100%" 
              height="100%" 
              style="border:0;" 
              allowfullscreen="" 
              loading="lazy"
            ></iframe>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="lg:col-span-2" data-aos="fade-left">
          <form @submit.prevent="sendEmail" class="space-y-6">
            <div class="grid md:grid-cols-2 gap-6">
              <div class="space-y-2">
                <label class="text-gray-400 text-sm font-medium ml-1">Your Name</label>
                <input 
                  v-model="form.name"
                  type="text" 
                  placeholder="John Doe"
                  required
                  class="w-full bg-[#1e293b]/50 border border-gray-800 rounded-xl px-6 py-4 text-white focus:outline-none focus:border-blue-500 transition-colors"
                >
              </div>
              <div class="space-y-2">
                <label class="text-gray-400 text-sm font-medium ml-1">Email Address</label>
                <input 
                  v-model="form.email"
                  type="email" 
                  placeholder="john@example.com"
                  required
                  class="w-full bg-[#1e293b]/50 border border-gray-800 rounded-xl px-6 py-4 text-white focus:outline-none focus:border-blue-500 transition-colors"
                >
              </div>
            </div>

            <div class="space-y-2">
              <label class="text-gray-400 text-sm font-medium ml-1">Subject</label>
              <input 
                v-model="form.subject"
                type="text" 
                placeholder="Project Inquiry"
                required
                class="w-full bg-[#1e293b]/50 border border-gray-800 rounded-xl px-6 py-4 text-white focus:outline-none focus:border-blue-500 transition-colors"
              >
            </div>

            <div class="space-y-2">
              <label class="text-gray-400 text-sm font-medium ml-1">Message</label>
              <textarea 
                v-model="form.message"
                rows="6" 
                placeholder="Tell me about your project..."
                required
                class="w-full bg-[#1e293b]/50 border border-gray-800 rounded-xl px-6 py-4 text-white focus:outline-none focus:border-blue-500 transition-colors resize-none"
              ></textarea>
            </div>

            <button 
              type="submit" 
              :disabled="isSubmitting"
              class="w-full md:w-auto px-12 py-4 bg-blue-600 hover:bg-blue-700 text-white font-bold rounded-xl transition-all shadow-lg shadow-blue-600/20 disabled:opacity-50 flex items-center justify-center"
            >
              <Send v-if="!isSubmitting" class="w-5 h-5 mr-2" />
              <Loader2 v-else class="w-5 h-5 mr-2 animate-spin" />
              {{ isSubmitting ? 'Sending...' : 'Send Message' }}
            </button>
            
            <p v-if="submitStatus" :class="[
              'text-sm font-medium transition-opacity duration-300',
              submitStatus.type === 'success' ? 'text-green-500' : 'text-red-500'
            ]">
              {{ submitStatus.message }}
            </p>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { Mail, Phone, MapPin, Send, Loader2 } from 'lucide-vue-next'
import emailjs from '@emailjs/browser'

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)
const submitStatus = ref(null)

const contactInfo = [
  { icon: Mail, label: 'Email Me', value: 'contact@mahedi.com' },
  { icon: Phone, label: 'Call Me', value: '+880 1234 567 890' },
  { icon: MapPin, label: 'Location', value: 'Dhaka, Bangladesh' }
]

const sendEmail = async () => {
  isSubmitting.value = true
  submitStatus.value = null

  try {
    // You'll need to replace these with your actual EmailJS credentials
    // const result = await emailjs.send(
    //   'YOUR_SERVICE_ID',
    //   'YOUR_TEMPLATE_ID',
    //   {
    //     from_name: form.name,
    //     from_email: form.email,
    //     subject: form.subject,
    //     message: form.message,
    //   },
    //   'YOUR_PUBLIC_KEY'
    // )

    // Simulating API call for demonstration
    await new Promise(resolve => setTimeout(resolve, 2000))

    submitStatus.value = {
      type: 'success',
      message: 'Thank you! Your message has been sent successfully.'
    }
    
    // Reset form
    form.name = ''
    form.email = ''
    form.subject = ''
    form.message = ''
  } catch (error) {
    submitStatus.value = {
      type: 'error',
      message: 'Something went wrong. Please try again later.'
    }
  } finally {
    isSubmitting.value = false
  }
}
</script>
