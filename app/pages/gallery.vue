<script setup lang="ts">
useSeoMeta({
  title: 'Gallery – PRINTED Hub 2025',
  description: 'Photos from PRINTED Hub 2025 in Rüdesheim am Rhein.',
})

const allImages = [
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

function shuffle<T>(arr: T[]): T[] {
  const a = [...arr]
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1))
    ;[a[i], a[j]] = [a[j], a[i]]
  }
  return a
}

const images = shuffle(allImages)

const lightboxIndex = ref<number | null>(null)

function openLightbox(index: number) {
  lightboxIndex.value = index
}

function closeLightbox() {
  lightboxIndex.value = null
}

function prev() {
  if (lightboxIndex.value === null) return
  lightboxIndex.value = (lightboxIndex.value - 1 + images.length) % images.length
}

function next() {
  if (lightboxIndex.value === null) return
  lightboxIndex.value = (lightboxIndex.value + 1) % images.length
}

function onKeydown(e: KeyboardEvent) {
  if (lightboxIndex.value === null) return
  if (e.key === 'Escape') closeLightbox()
  if (e.key === 'ArrowLeft') prev()
  if (e.key === 'ArrowRight') next()
}

onMounted(() => window.addEventListener('keydown', onKeydown))
onUnmounted(() => window.removeEventListener('keydown', onKeydown))
</script>

<template>
  <UPageSection
    description="Impressions from PRINTED Hub 2025 in Rüdesheim am Rhein."
    headline="PRINTED Hub 2025"
    title="Gallery"
  >
    <!-- Masonry grid via CSS columns -->
    <div class="columns-1 gap-4 sm:columns-2 md:columns-3">
      <div
        v-for="(src, index) in images"
        :key="src"
        class="mb-4 break-inside-avoid cursor-pointer overflow-hidden rounded-lg"
        @click="openLightbox(index)"
      >
        <NuxtImg
          :alt="'PRINTED Hub 2025'"
          class="w-full transition-transform duration-300 hover:scale-105"
          loading="lazy"
          :src="src"
        />
      </div>
    </div>

    <!-- Lightbox overlay -->
    <Teleport to="body">
      <Transition name="lightbox">
        <div
          v-if="lightboxIndex !== null"
          class="fixed inset-0 z-50 flex items-center justify-center bg-black/90"
          @click.self="closeLightbox"
        >
          <!-- Close button -->
          <button
            class="absolute top-4 right-4 text-white/70 hover:text-white transition-colors p-2"
            @click="closeLightbox"
          >
            <UIcon name="i-lucide-x" class="size-8" />
          </button>

          <!-- Prev button -->
          <button
            class="absolute left-4 text-white/70 hover:text-white transition-colors p-2"
            @click="prev"
          >
            <UIcon name="i-lucide-chevron-left" class="size-10" />
          </button>

          <!-- Image -->
          <img
            v-if="lightboxIndex !== null"
            :src="images[lightboxIndex]"
            alt="PRINTED Hub 2025"
            class="max-h-[90vh] max-w-[90vw] rounded-lg object-contain shadow-2xl"
          />

          <!-- Next button -->
          <button
            class="absolute right-4 text-white/70 hover:text-white transition-colors p-2"
            @click="next"
          >
            <UIcon name="i-lucide-chevron-right" class="size-10" />
          </button>

          <!-- Counter -->
          <div class="absolute bottom-4 text-white/50 text-sm">
            {{ (lightboxIndex ?? 0) + 1 }} / {{ images.length }}
          </div>
        </div>
      </Transition>
    </Teleport>
  </UPageSection>
</template>

<style scoped>
.lightbox-enter-active,
.lightbox-leave-active {
  transition: opacity 0.2s ease;
}
.lightbox-enter-from,
.lightbox-leave-to {
  opacity: 0;
}
</style>
