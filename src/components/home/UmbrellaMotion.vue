<template>
  <div class="umbrella" ref="umbrella">
    <div class="umbrella__outline" ref="umbrellasvg">
      <UmbrellaOutline />
    </div>

    <div class="umbrella__text-container">
      <div class="umbrella__text" ref="text">
        <h2>Beautiful umbrellas, built to last.</h2>
        <br /><br />
        <h2>Providing joy and confidence in life's vulnerable moments.</h2>
      </div>
    </div>
    <div class="umbrella__filled" ref="filling">
      <div class="umbrella__filled--fill"></div>
      <div class="umbrella__filled--empty"></div>
    </div>
    <img
      class="umbrella__filled-img"
      src="@/assets/images/3dmotion/Blunt_HPFinal0010_0010.jpg"
    />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import UmbrellaOutline from "../svg/UmbrellaOutline.vue";

const umbrella = ref();
const umbrellasvg = ref();
const text = ref();
const filling = ref();

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});

let lastScrollTop = window.scrollY || document.documentElement.scrollTop;
let isTextDisappeared = false;

function handleScroll() {
  let y = umbrella.value.getBoundingClientRect().y;
  if (y <= 0) {
    const scrollTopPosition =
      window.scrollY || document.documentElement.scrollTop;

    if (scrollTopPosition >= lastScrollTop) {
      if (text.value.style.transform) {
        text.value.style.transform = "translate(0, -200%)";
        isTextDisappeared = true;
      } else {
        text.value.style.transform = "translate(0, 72px)";
      }
      umbrellasvg.value.style.transform = "scale(1, 1)";
    } else if (scrollTopPosition < lastScrollTop) {
      text.value.style.transform = "translate(0, 200%)";
    }
    lastScrollTop = scrollTopPosition <= 0 ? 0 : scrollTopPosition;
  }
  if (isTextDisappeared) {
    filling.value.scrollTo(0, filling.value.scrollTop + 10);
  }
}
</script>

<style lang="scss">
.umbrella {
  width: 100%;
  height: 100vh;
  background-color: #efefef;
  position: relative;
  overflow: hidden;
  padding-top: 72px;

  &__outline {
    top: 0;
    position: sticky;
    transition: 1.5s;
    transform: scale(1.3, 1.3);
    z-index: 10;
  }

  &__filled-img {
    top: -70px;
    left: 0;
    position: absolute;
    width: 100%;
    transform: scale(0.76, 0.76);
    z-index: 8;
    transition: 1.5s;
  }

  &__filled {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    overflow: auto;
    z-index: 9;

    &--fill {
      position: relative;
      width: 100%;
      height: 200vh;
      background-color: #efefef;
      z-index: 9;
    }

    &--empty {
      position: relative;
      width: 100%;
      height: 100vh;
      background-color: transparent;
      z-index: 9;
    }
  }

  &__text-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
  }

  &__text {
    position: relative;
    top: 0;
    max-width: 1085px;
    height: 100%;
    transform: translate(0, 200%);
    transition: 1.5s;
    margin: auto;
    z-index: 11;

    h2 {
      font-size: 95px;
      font-weight: 600;
      line-height: 0.95em;
      z-index: 11;
    }
  }
}
</style>
