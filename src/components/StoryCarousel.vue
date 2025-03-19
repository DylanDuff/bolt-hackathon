<script setup lang="ts">
import { ref, onMounted } from 'vue'

const currentSlide = ref(0)
const slides = ['location.png']

const progress = ref(0)
let interval: any

onMounted(() => {
  startProgress()
})

const startProgress = () => {
  clearInterval(interval)
  progress.value = 0
  interval = setInterval(() => {
    progress.value += 1
    if (progress.value >= 100) {
      progress.value = 0
      nextSlide()
    }
  }, 50)
}

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length
  startProgress()
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length
  startProgress()
}
</script>

<template>
  <div class="absolute overflow-clip p-4 h-full w-full">
    <!-- Progress bars -->
    <div class="absolute top-4 left-4 right-4 flex gap-2 z-10">
      <div
        v-for="(slide, index) in slides"
        :key="index"
        class="h-1 flex-1 rounded-full bg-white/30 overflow-hidden"
      >
        <div
          class="h-full bg-white transition-all duration-100"
          :style="{
            width: index === currentSlide ? `${progress}%` : index < currentSlide ? '100%' : '0%',
          }"
        ></div>
      </div>
    </div>

    <!-- Slides -->
    <div class="absolute w-full h-full">
      <img
        v-for="(slide, index) in slides"
        :key="slide"
        :src="slide"
        :class="[
          'absolute inset-0 w-full h-full object-cover transition-opacity duration-300',
          index === currentSlide ? 'opacity-100' : 'opacity-0',
        ]"
        @click="nextSlide"
      />
    </div>

    <!-- Navigation Arrows -->
    <div class="absolute bottom-6 right-6 flex gap-2 z-10">
      <button
        @click="prevSlide"
        class="w-10 h-10 rounded-full nav-arrow bg-white/10 hover:bg-white/20 transition-colors flex items-center justify-center"
      >
        ←
      </button>
      <button
        @click="nextSlide"
        class="w-10 h-10 rounded-full nav-arrow bg-white/10 hover:bg-white/20 transition-colors flex items-center justify-center"
      >
        →
      </button>
    </div>
  </div>
</template>
