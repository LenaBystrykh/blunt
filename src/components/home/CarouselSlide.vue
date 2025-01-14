<template>
  <div class="slide" :style="{ backgroundColor: slide.color }">
    <div class="slide__image" :style="{ color: slide.color }">
      <img :src="slide.src" />
      <CarouselWaves class="slide__waves" />
    </div>
    <div class="slide__right">
      <div class="slide__content">
        <h3>{{ slide.title }}</h3>
        <p>{{ slide.text }}</p>
        <div class="slide__actions">
          <button class="slide__button slide__button--white">Shop Now</button>
          <button class="slide__button slide__button--transparent">
            View Limited Edition
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import CarouselWaves from "@/components/svg/CarouselWaves.vue";
defineProps({
  slide: Object,
});
</script>

<style lang="scss">
.slide {
  display: flex;
  width: 100%;
  height: 840px;

  &__image {
    flex: 6;
    position: relative;
    height: 100%;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  &__waves {
    position: absolute;
    right: -5%;
    top: 0;
  }

  &__right {
    flex: 5;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  &__content {
    text-align: left;
    max-width: 440px;
    color: white;
  }

  h3 {
    text-align: left;
    font-size: 75px;
    line-height: 1em;
    margin-bottom: 14px;
    font-weight: 600;
  }

  p {
    width: 100%;
    letter-spacing: 0.02em;
    font-weight: 500;
    margin-bottom: 50px;
  }

  &__actions {
    display: flex;
  }
  &__button {
    flex: 1;
    font-size: 14px;
    line-height: 18px;
    padding: 16px;
    min-width: 170px;
    text-align: center;
    border-radius: 5px;
    transition: 0.3s;
    display: inline-block;
    font-weight: 600;
    border: none;
    cursor: pointer;
    text-decoration: none;

    &--white {
      background: white;
      color: #262525;

      &:hover {
        color: white;
        background: #232323;
      }
    }

    &--transparent {
      margin-left: 10px;
      color: white;
      background: rgba(255, 255, 255, 0.2);

      &:hover {
        color: #262525;
        background-color: white;
      }
    }
  }
}
</style>
