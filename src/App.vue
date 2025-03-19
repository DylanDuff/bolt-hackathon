<script setup lang="ts">
import { ref } from 'vue'
import GridView from './components/GridView.vue'
import StoryCarousel from './components/StoryCarousel.vue'
import JudgesView from './components/JudgesView.vue'

const selectedOption = ref<'build' | 'judges'>('build')
const currentView = ref<'home' | 'grid'>('home')

const handleNext = () => {
  if (selectedOption.value === 'build') {
    currentView.value = 'grid'
  } else if (selectedOption.value === 'judges') {
    showJudges.value = true
  }
}

const showJudges = ref(false)

const handleJudgesClick = () => {
  showJudges.value = true
}
</script>

<template>
  <Transition name="fade" mode="out-in">
    <GridView v-if="currentView === 'grid'" @back="currentView = 'home'" />

    <JudgesView v-else-if="showJudges" @back="showJudges = false" />

    <div v-else class="min-h-screen flex items-center overflow-hidden text-white p-8 font-figtree">
      <div class="grid grid-cols-2 w-full justify-between">
        <Transition name="fade">
          <div class="w-full flex flex-col gap-10">
            <div class="max-w-4xl flex gap-4 flex-col" style="margin-top: auto">
              <div class="animate-title opacity-0 animation-delay-450">
                <span
                  class="inline-block z-10 px-3 py-1 rounded-full border border-white/60 text-xs text-white/60"
                >
                  Date: TBD
                </span>
              </div>

              <h1 class="text-6xl mb-6 mt-6 leading-[1.1] flex flex-col">
                <span class="animate-title opacity-0">The Worlds</span>
                <span class="animate-title opacity-0 animation-delay-150">Biggest Hackathon</span>
              </h1>
            </div>

            <div class="mt-16 z-10 space-y-3 flex flex-col gap-5 max-w-md">
              <button
                class="option-button opacity-0 animate-title animation-delay-500"
                :class="
                  selectedOption === 'build' ? 'option-button--active' : 'option-button--inactive'
                "
                @click="selectedOption = 'build'"
              >
                <span class="text-xl">I'm ready to build</span>
                <div class="avatar-group">
                  <img class="judge-art language" src="/vue.png" alt="" />
                  <img class="judge-art language" src="/react.png" alt="" />
                  <img class="judge-art language" src="/svelte.png" alt="" />
                </div>
              </button>

              <button
                class="option-button opacity-0 animate-title animation-delay-600"
                :class="
                  selectedOption === 'judges' ? 'option-button--active' : 'option-button--inactive'
                "
                @click="selectedOption = 'judges'"
              >
                <span class="text-xl">Meet the judges</span>
                <div class="avatar-group">
                  <img class="judge-art" src="/prime.jpeg" alt="" />
                  <img class="judge-art" src="/prime.jpeg" alt="" />
                  <img class="judge-art" src="/prime.jpeg" alt="" />
                </div>
              </button>
              <div class="flex flex-col items-end w-full mt-8">
                <button
                  class="px-8 z-10 py-3 rounded-full bg-white/10 hover:bg-white/20 transition-colors text-white"
                  @click="handleNext"
                >
                  Next →
                </button>
              </div>
            </div>

            <div class="flex items-center text-l gap-3 text-gray-500" style="margin-top: auto">
              <span class="text-xl animate-title justify-self-end opacity-0 animation-delay-450"
                >Sponsored By</span
              >
              <div class="avatar-group">
                <div
                  class="avatar avatar--active opacity-0 animate-scale animation-delay-500"
                ></div>
                <div
                  class="avatar avatar--active opacity-0 animate-scale animation-delay-550"
                ></div>
                <div
                  class="avatar avatar--active opacity-0 animate-scale animation-delay-600"
                ></div>
              </div>
            </div>
          </div>
        </Transition>

        <div class="carousel min-h-[90vh] z-20 rounded-xl carousel-card animate-slide-in opacity-0">
          <StoryCarousel />
        </div>
      </div>
    </div>
  </Transition>
</template>
