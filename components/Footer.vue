<template>
  <footer class="footer flex">
    <div class="footer__inner flex flex-col flex-auto items-center justify-center">
      <div class="footer__container footer__container--logo">
        <img src="/footer-logo.png" alt="quicktell logotype" class="footer__logo">
      </div>
      <div class="footer__container footer__container--content">
        <span class="footer__copyright">©2022</span>
      </div>
    </div>
  </footer>
</template>

<style scoped lang="scss">
.footer {
  &__inner {
    padding: 2.5rem 5.5rem;
  }

  &__copyright {
    font-size: 1.25rem;
  }
}
</style>
