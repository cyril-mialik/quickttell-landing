<script setup lang="ts">
import type { PropType } from 'vue'

defineProps({
  tag: {
    type: String as PropType<string>,
    required: false,
    default: 'ul',
    validator(value: string) {
      return ['ul', 'ol'].includes(value)
    },
  },

  list: {
    type: Array as PropType<any[]>,
    required: true,
  },
})
</script>

<template>
  <component :is="tag" class="list flex">
    <slot :list="list" />
  </component>
</template>
