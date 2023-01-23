<script setup lang="ts">
const props = defineProps<{
  isActive: boolean
}>()

const emit = defineEmits(['click'])

const handleClick = (): void => {
  emit('click')
}

defineExpose({
  handleClick,
})
</script>

<template>
  <button
    value="burger-button"
    type="button"
    class="burger-button flex justify-center items-center color-dark"
    @click="handleClick"
  >
    <span
      class="burger-button__line bg-dark"
      :class="{
        'burger-button__line--active': isActive,
      }"
    />
  </button>
</template>

<style scoped lang="scss">
.burger-button {
  &__line {
    position: relative;
    width: 1.2rem;
    height: 2px;
    transition: background 0.25s ease-out;

    &::before,
    &::after {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: currentColor;
      transition: transform 0.25s ease-out;
    }

    &::before {
      transform: translateY(-5px);
    }

    &::after {
      transform: translateY(5px);
    }

    &--active {
      background: transparent;

      &::before {
        transform: translateY(0) rotate(-45deg);
      }

      &::after {
        transform: translateY(0) rotate(45deg);
      }
    }
  }
}
</style>
