<script setup lang="ts">
import { ref } from 'vue'

const frameworks = [
  {
    name: 'Vue',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg',
  },
  {
    name: 'React',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg',
  },
  {
    name: 'Angular',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/angularjs/angularjs-original.svg',
  },
  {
    name: 'Svelte',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/svelte/svelte-original.svg',
  },
  {
    name: 'Next.js',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nextjs/nextjs-original.svg',
  },
  {
    name: 'Node.js',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg',
  },
  {
    name: 'TypeScript',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg',
  },
  {
    name: 'Nuxt',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nuxtjs/nuxtjs-original.svg',
  },
  {
    name: 'Tailwind',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tailwindcss/tailwindcss-original.svg',
  },
]

const selectedTile = ref(0)
const emit = defineEmits(['back'])
</script>

<template>
  <div class="min-h-screen flex flex-col items-center gap-10 justify-center p-8 font-figtree">
    <button
      @click="emit('back')"
      class="absolute z-10 top-8 left-8 px-4 py-2 rounded-full bg-white/10 hover:bg-white/20 transition-colors text-white flex items-center gap-2"
    >
      ← Back
    </button>

    <div class="text-center flex-col flex gap-4">
      <span class="text-gray-400 text-sm mb-4 block">bolt</span>
      <h1 class="text-6xl font-semibold text-white">Let's Vibe.</h1>
    </div>

    <div class="z-10 grid grid-cols-3 gap-4 max-w-3xl">
      <button
        v-for="(framework, i) in frameworks"
        :key="framework.name"
        class="option-button relative group"
        :class="selectedTile === i ? 'option-button--active' : 'option-button--inactive'"
        @click="selectedTile = i"
      >
        <div class="flex flex-col items-center justify-center min-w-28 w-full h-full gap-3">
          <img :src="framework.icon" :alt="framework.name" class="w-12 h-12 object-contain" />
          <span class="text-sm opacity-60 group-hover:opacity-100 transition-opacity">
            {{ framework.name }}
          </span>
        </div>
        <div
          class="absolute top-3 right-3 w-2 h-2 rounded-full border indicator border-white/20"
        ></div>
      </button>
    </div>
  </div>
</template>
