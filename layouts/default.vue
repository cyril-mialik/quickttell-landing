<script setup lang="ts">
import { useMediaQuery } from '@vueuse/core'

const isDesktop = useMediaQuery('(min-width: 1024px)')

defineExpose({
  isDesktop,
})
</script>

<template>
  <div id="default" class="layout flex flex-col flex-auto bg-primary">
    <Header class="layout__header" :is-desktop="isDesktop" />
    <main class="layout__content flex flex-auto">
      <slot />
    </main>
    <Footer class="layout__footer" />
  </div>
</template>
