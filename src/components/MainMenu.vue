<template>
  <nav class="main-menu">
    <div class="main-menu__left">
      <p class="main-menu__item">Shop</p>
      <p class="main-menu__item">Umbrellas</p>
      <p class="main-menu__item">About</p>
      <p class="main-menu__item">Sustainability</p>
    </div>
    <div class="main-menu__logo">
      <MainLogo />
    </div>
    <div class="main-menu__right">
      <p class="main-menu__item">Care & Support</p>
      <div class="main-menu__separator" />
      <p class="main-menu__item">Ship to</p>
      <div class="main-menu__separator" />
      <div class="main-menu__item main-menu__icons">
        <SearchIcon />
        <AccountIcon />
        <CartIcon />
      </div>
    </div>
  </nav>
</template>
<script setup>
import MainLogo from "@/components/svg/MainLogo.vue";
import SearchIcon from "@/components/svg/SearchIcon.vue";
import AccountIcon from "@/components/svg/AccountIcon.vue";
import CartIcon from "@/components/svg/CartIcon.vue";
</script>

<style lang="scss">
.main-menu {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: absolute;
  top: 0;
  width: 100%;
  height: 60px;
  color: white;
  z-index: 100;
  padding-left: 24px;

  &__left {
    display: flex;
    width: calc((100% - 97px) / 2);
  }

  &__right {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    width: calc((100% - 97px) / 2);
  }

  &__logo svg path {
    fill: white;
  }

  &__item {
    margin-right: 24px;
    cursor: pointer;
    font-size: 15px;
    font-weight: 500;
    line-height: 24px;
    letter-spacing: 0.02em;

    svg {
      margin-right: 24px;

      &:last-of-type {
        margin: 0;
      }

      path {
        fill: white;
      }
    }
  }

  &__separator {
    width: 1px;
    height: 15px;
    margin-right: 24px;
    background-color: rgba(255, 255, 255, 0.2);
  }
}
</style>
