<script setup lang="ts">
const route = useRoute()

const items = computed(() => [
  {
    label: 'Schedule',
    to: '/schedule',
    active: route.path.startsWith('/schedule') || route.path.startsWith('/talks'),
  },
  {
    label: 'Speakers',
    to: '/speakers',
    active: route.path.startsWith('/speakers'),
  },
  {
    label: 'Gallery',
    to: '/gallery',
    active: route.path.startsWith('/gallery'),
  },
  {
    label: 'FAQ',
    to: '/faq',
    active: route.path.startsWith('/faq'),
  },
])
</script>

<template>
  <UHeader mode="slideover">
    <template #left>
      <ULink
        aria-label="Home"
        class="mr-0 md:mr-8"
        to="/"
      >
        <AppLogo class="w-auto h-6 shrink-0" />
      </ULink>

      <UNavigationMenu
        class="hidden lg:inline-flex"
        :items="items"
        variant="link"
      />
    </template>

    <template #right>
      <UButton
        class="hidden lg:inline-flex"
        color="primary"
        label="PRINTED Hub 2026"
        to="https://printed-europe.com"
        target="_blank"
        variant="solid"
      />
    </template>

    <template #body>
      <UNavigationMenu
        class="-mx-2.5"
        :items="items"
        orientation="vertical"
      />

      <USeparator class="my-6" />

      <UButton
        block
        class="mb-3"
        color="primary"
        label="PRINTED Hub 2026"
        to="https://printed-europe.com"
        target="_blank"
        variant="solid"
      />
    </template>
  </UHeader>
</template>
