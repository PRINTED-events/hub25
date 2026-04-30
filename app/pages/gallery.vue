<script setup lang="ts">
useSeoMeta({
  title: 'Gallery – PRINTED Hub 2025',
  description: 'Photos from PRINTED Hub 2025 in Rüdesheim am Rhein.',
})

const images = [
  '/gallery/printedhub25-007.jpg',
  '/gallery/printedhub25-010.jpg',
  '/gallery/printedhub25-011.jpg',
  '/gallery/printedhub25-014.jpg',
  '/gallery/printedhub25-015.jpg',
  '/gallery/printedhub25-016.jpg',
  '/gallery/printedhub25-019.jpg',
  '/gallery/printedhub25-020.jpg',
  '/gallery/printedhub25-021.jpg',
  '/gallery/printedhub25-027.jpg',
  '/gallery/printedhub25-029.jpg',
  '/gallery/printedhub25-032.jpg',
  '/gallery/printedhub25-035.jpg',
  '/gallery/printedhub25-037.jpg',
  '/gallery/printedhub25-038.jpg',
  '/gallery/printedhub25-040.jpg',
  '/gallery/printedhub25-043.jpg',
  '/gallery/printedhub25-044.jpg',
  '/gallery/printedhub25-045.jpg',
  '/gallery/printedhub25-052.jpg',
  '/gallery/printedhub25-053.jpg',
  '/gallery/printedhub25-054.jpg',
  '/gallery/printedhub25-055.jpg',
  '/gallery/printedhub25-056.jpg',
  '/gallery/printedhub25-060.jpg',
  '/gallery/printedhub25-061.jpg',
  '/gallery/printedhub25-080.jpg',
  '/gallery/printedhub25-083.jpg',
  '/gallery/printedhub25-085.jpg',
  '/gallery/printedhub25-090.jpg',
  '/gallery/printedhub25-095.jpg',
  '/gallery/printedhub25-096.jpg',
  '/gallery/printedhub25-100.jpg',
  '/gallery/printedhub25-101.jpg',
  '/gallery/printedhub25-106.jpg',
  '/gallery/printedhub25-107.jpg',
  '/gallery/printedhub25-112.jpg',
  '/gallery/printedhub25-116.jpg',
  '/gallery/printedhub25-119.jpg',
  '/gallery/printedhub25-123.jpg',
  '/gallery/printedhub25-131.jpg',
]
</script>

<template>
  <UPageSection
    description="Impressions from PRINTED Hub 2025 in Rüdesheim am Rhein."
    headline="PRINTED Hub 2025"
    title="Gallery"
  >
    <div class="grid grid-cols-1 gap-4 sm:grid-cols-2 md:grid-cols-3">
      <div
        v-for="src in images"
        :key="src"
        class="relative aspect-4/3 overflow-hidden rounded-lg bg-neutral-800"
      >
        <NuxtImg
          :alt="'PRINTED Hub 2025'"
          class="absolute inset-0 h-full w-full object-cover transition-transform duration-300 hover:scale-105"
          loading="lazy"
          :src="src"
        />
      </div>
    </div>
  </UPageSection>
</template>
