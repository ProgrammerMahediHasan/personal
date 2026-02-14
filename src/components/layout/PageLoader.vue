<template>
  <Transition name="fade">
    <div v-if="isLoading" class="fixed inset-0 z-[100] bg-[#0f172a] flex items-center justify-center">
      <div class="relative">
        <!-- Main Logo/Text -->
        <div class="text-4xl font-bold text-white tracking-widest animate-pulse">
          M<span class="text-blue-500">H</span>A
        </div>
        
        <!-- Loading Bar -->
        <div class="absolute -bottom-4 left-0 w-full h-1 bg-gray-800 rounded-full overflow-hidden">
          <div class="h-full bg-blue-600 animate-loading-bar"></div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script setup>
defineProps({
  isLoading: Boolean
})
</script>

<style scoped>
.animate-loading-bar {
  width: 0%;
  animation: loading 1.5s ease-in-out infinite;
}

@keyframes loading {
  0% { width: 0%; left: 0; }
  50% { width: 100%; left: 0; }
  100% { width: 0%; left: 100%; }
}

.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-leave-to {
  opacity: 0;
}
</style>
