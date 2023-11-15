<template>
  <div class="carousel-section">
    <div class="carousel-section__bg">
      <img
        src="@/assets/images/home-carousel.jpg"
        class="carousel-section__img"
        :class="{ active: slide === 1 }"
      />
      <img
        src="@/assets/images/home-carousel-2.webp"
        class="carousel-section__img"
        :class="{ active: slide === 2 }"
      />
      <img
        src="@/assets/images/home-carousel-3.webp"
        class="carousel-section__img"
        :class="{ active: slide === 3 }"
      />
    </div>
    <div class="carousel-section__content">
      <div class="carousel-section__categories">
        <p class="carousel-section__category" :class="{ active: slide === 1 }">
          Metro
        </p>
        <p class="carousel-section__category" :class="{ active: slide === 2 }">
          Classic
        </p>
        <p class="carousel-section__category" :class="{ active: slide === 3 }">
          Sport
        </p>
      </div>
      <div class="carousel-section__info">
        <button class="carousel-section__button">Shop umbrellas</button>
        <div class="carousel-section__text-container">
          <p class="carousel-section__text" :class="{ active: slide === 1 }">
            Compact, collapsible and convenient, the BLUNT Metro is always at
            hand to keep you protected on the go.
          </p>
          <p class="carousel-section__text" :class="{ active: slide === 2 }">
            Inspired by tradition, designed for the future. The original
            full-length BLUNT Classic is ideal for those who need impromptu
            protection in a serious downpour.
          </p>
          <p class="carousel-section__text" :class="{ active: slide === 3 }">
            Never let the rain stop play. Strong and athletic, the BLUNT Sport
            is made for those truly committed to the golf course or enduring the
            elements on the Saturday morning sidelines.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const slide = ref(1);
setInterval(function () {
  changeSlide();
}, 3000);

function changeSlide() {
  if (slide.value < 3) {
    slide.value++;
  } else {
    slide.value = 1;
  }
}
</script>

<style lang="scss">
.carousel-section {
  width: 100%;
  height: 90vh;
  position: relative;
  background-color: #f6f6f6;

  &__bg,
  &__content {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
  }

  &__content {
    z-index: 11;
    display: flex;
    flex-direction: column;
    padding: 80px 70px 80px 90px;
  }

  &__img {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    top: 0;
    left: 0;
    z-index: 10;
    border-radius: 20px 20px 0 0;
    opacity: 0;
    transition: 0.5s;

    &.active {
      opacity: 1;
    }
  }

  &__categories {
    text-align: left;
    margin-top: auto;
    padding-bottom: 97px;
  }

  &__category {
    font-size: 95px;
    line-height: 0.95em;
    font-weight: 600;
    color: white;
    opacity: 0.5;
    transition: 0.5s;

    &.active {
      opacity: 1;
    }
  }

  &__info {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
  }

  &__text-container {
    width: 390px;
    text-align: left;
    color: white;
    font-size: 18px;
    font-weight: 500;
    position: relative;
  }

  &__text {
    position: absolute;
    bottom: 0;
    left: 0;
    opacity: 0;
    transition: 0.5s;

    &.active {
      opacity: 1;
    }
  }

  &__button {
    width: 170px;
    height: 50px;
    padding: 16px;
    border-radius: 5px;
    outline: none;
    border: none;
    transition: 0.3s;
    cursor: pointer;
    font-size: 14px;
    font-weight: 600;
    background-color: white;
    color: #262525;

    &:hover {
      background-color: #262525;
      color: white;
    }
  }
}
</style>
