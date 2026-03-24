<template>
  <CTASectionTwoBlocks
    label="Label"
    title="Mandatory title about the call-to-action here"
    body-copy="Optional body copy goes here."
    cta-text="Optional button"
    cta-url="#"
    :blocks="blocks"
  />
</template>

<script setup lang="ts">
import CTASectionTwoBlocks from './components/CTASectionTwoBlocks.vue'

interface Block {
  id: number
  image: string
  title: string
  text: string
  url: string
}

const blocks: Block[] = [
  {
    id: 1,
    image: 'https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2?w=800&q=80',
    title: 'Title',
    text: 'Supporting text about the call-to-action goes here.',
    url: '#',
  },
  {
    id: 2,
    image: 'https://images.unsplash.com/photo-1529156069898-49953e39b3ac?w=800&q=80',
    title: 'Title',
    text: 'Supporting text about the call-to-action goes here.',
    url: '#',
  },
]
</script>