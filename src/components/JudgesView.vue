<script setup lang="ts">
defineEmits(['back'])

const judges = [
  {
    name: 'The Primeagen',
    bio: 'Veniam irure aliqua sint cupidatat elit incididunt in qui esse. Sint velit officia nostrud velit fugiat est nisi eiusmod. Amet dolore sit laboris fugiat incididunt anim cupidatat magna velit.',
  },
  // ... repeat for other judges
]
</script>

<template>
  <div class="p-12 flex flex-col gap-4 text-white">
    <button
      @click="$emit('back')"
      class="absolute top-8 z-20 left-8 px-4 py-2 rounded-full bg-white/10 hover:bg-white/20 transition-colors text-white flex items-center gap-2"
    >
      ← Back
    </button>

    <div class="flex pt-15 pb-5 flex-col gap-2">
      <h2 class="text-4xl font-semibold mb-4">Meet The Judges</h2>
      <p class="text-gray-400 mb-12 max-w-xl">
        Irure consectetur aliquip voluptate laboris proident sint in laborum.
      </p>
    </div>

    <div class="grid z-20 grid-cols-3 gap-8">
      <div
        v-for="(judge, index) in judges"
        :key="index"
        class="flex gap-4 items-start justify-items-start option-button flex-row rounded-2xl transition-colors"
      >
        <img
          src="/prime.jpeg"
          alt="Judge"
          class="w-24 h-24aspect-square rounded-xl mb-4 object-cover"
        />
        <div class="flex flex-col gap-2">
          <h3 class="text-xl font-medium mb-2">{{ judge.name }}</h3>
          <p class="text-gray-400 text-sm">{{ judge.bio }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
