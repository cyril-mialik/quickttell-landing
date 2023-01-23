<template>
  <div id="index" class="page flex flex-auto">
    <Suspense>
      <div class="page__inner flex flex-auto">
        <section class="page__block flex flex-auto bg-dark-gradient-primary">
          12
        </section>
      </div>

      <template #fallback>
        <div op50 italic>
          <span animate-pulse>Loading...</span>
        </div>
      </template>
    </Suspense>
  </div>
</template>

<style scoped lang="scss">
.page {
  &__block {
    border-radius: 3rem;
  }
}
</style>
