<script setup lang="ts">
defineProps<{
  isDesktop: boolean
}>()

const isMenu = ref<boolean>(false)
const menuList = ref<string[]>(['Сервисы', 'Интеграции', 'Тарифы', 'О нас', 'Блог', 'Поддержка', 'Контакты'])

const handleToggleMenu = (): void => {
  isMenu.value = !isMenu.value
}

defineExpose({
  isMenu,
  menuList,

  handleToggleMenu,
})
</script>

<template>
  <header class="head flex" :class="{ 'head--menu': isMenu }">
    <div
      class="head__inner flex flex-auto"
      :class="{ 'flex-col': !isDesktop }"
    >
      <div class="head__container head__container--logo flex flex-auto justify-between">
        <img src="/logo.png" alt="quicktell logotype" class="head__logo">

        <burger-button
          class="head__burger"
          role="combobox"
          aria-controls="menu"
          aria-autocomplete="list"
          aria-activedescendant=""
          :is-active="isMenu"
          :aria-expanded="isMenu"
          @click="handleToggleMenu"
        />
      </div>

      <nav v-if="isMenu" id="menu" :aria-hidden="!isMenu" class="head__container head__container--content">
        <List :list="menuList" class="head__list flex-col">
          <template #default="{ list }">
            <list-item v-for="item in list" :key="item" class="head__list-item justify-between items-center">
              <nuxt-link class="head__link font-500">
                {{ item }}
              </nuxt-link>
            </list-item>
          </template>
        </List>
      </nav>
    </div>
  </header>
</template>

<style scoped lang="scss">
.head {
  flex: 0 1 5.5rem;

   &--menu {
    position: fixed;
    width: 100%;
    height: 100%;
  }

  &__inner {
    padding: 1.5rem;
  }

  &__burger {
    flex: 0 1 2.5rem;
    padding: 0.3125rem;
  }

  &__container {
    &--logo {
      flex: 0 0 2.5rem;
    }

    &--content {
      flex: auto;
      padding-top: 1.5rem;
    }
  }
}
</style>
