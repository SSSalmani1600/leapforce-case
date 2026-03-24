<template>
  <section class="bg-cream py-20 px-6">
    <!-- Header -->
    <div class="text-center max-w-xl mx-auto mb-14">
      <span v-if="label" class="text-xs text-gray-400 tracking-widest uppercase block mb-5">
        {{ label }}
      </span>
      <h2
        class="font-serif font-bold text-4xl md:text-5xl leading-tight text-gray-900 mb-5"
        v-html="formattedTitle"
      ></h2>
      <p v-if="bodyCopy" class="text-gray-500 text-base mb-5">{{ bodyCopy }}</p>
      <a
        v-if="ctaText"
        :href="ctaUrl"
        class="text-coral text-sm inline-flex items-center gap-1 hover:gap-2 transition-all duration-200"
      >
        {{ ctaText }} &rarr;
      </a>
    </div>

    <!-- Two blocks -->
    <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-3">
      <a
        v-for="block in blocks"
        :key="block.id"
        :href="block.url || '#'"
        class="relative overflow-hidden rounded group block"
      >
        <img
          :src="block.image"
          :alt="block.title"
          class="w-full aspect-[4/3] object-cover transition-transform duration-500 group-hover:scale-105"
        />
        <!-- Gradient overlay -->
        <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-black/10 to-transparent"></div>
        <!-- Text + arrow -->
        <div class="absolute bottom-0 left-0 right-0 p-5 flex justify-between items-end">
          <div class="pr-4">
            <h3 class="text-white font-bold text-lg leading-tight">{{ block.title }}</h3>
            <p class="text-white/80 text-sm mt-1">{{ block.text }}</p>
          </div>
          <div class="border border-white/60 text-white w-9 h-9 flex items-center justify-center flex-shrink-0 group-hover:bg-white group-hover:text-black transition-colors duration-200">
            &rarr;
          </div>
        </div>
      </a>
    </div>
  </section>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  label:    { type: String, default: '' },
  title:    { type: String, default: '' },
  bodyCopy: { type: String, default: '' },
  ctaText:  { type: String, default: '' },
  ctaUrl:   { type: String, default: '#' },
  blocks:   { type: Array,  default: () => [] },
})

// Last word of title becomes italic (matches Figma design)
const formattedTitle = computed(() => {
  if (!props.title) return ''
  const words = props.title.split(' ')
  const last = words.pop()
  return `${words.join(' ')} <em>${last}</em>`
})
</script>