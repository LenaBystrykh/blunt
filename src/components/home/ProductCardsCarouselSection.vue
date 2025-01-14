<template>
  <div class="cards-carousel-section">
    <div class="cards-carousel-section__header">
      <h2 class="cards-carousel-section__title">All Umbrellas</h2>
      <div class="cards-carousel-section__actions">
        <SlideArrow
          class="cards-carousel-section__arrow"
          :class="{ disabled: currentSlide <= 1 }"
          @click="prev"
          style="transform: scaleX(-1)"
        />
        <SlideArrow
          class="cards-carousel-section__arrow"
          :class="{ disabled: currentSlide === 5 }"
          @click="next"
        />
        <button class="cards-carousel-section__button">Shop Collection</button>
      </div>
    </div>
    <Carousel ref="carousel" v-model="currentSlide" :items-to-show="3">
      <Slide v-for="card in products" :key="card.id">
        <CarouselCard :card="card" />
      </Slide>
    </Carousel>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide } from "vue3-carousel";
import CarouselCard from "@/components/home/CarouselCard.vue";
import SlideArrow from "../svg/SlideArrow.vue";

const carousel = ref(null);
const currentSlide = ref(0);

const products = reactive([
  {
    id: 1,
    title: "Metro",
    price: 129,
    src: "/blunt/cards/card-yellow.webp",
    srcHovered: "/blunt/cards/card-yellow-hover.webp",
    colorStyle: "background-color: #facc52",
    link: "https://bluntumbrellas.co.nz/products/2020-blunt-metro",
  },
  {
    id: 2,
    title: "Metro UV",
    price: 139,
    text: "uv protection",
    src: "/blunt/cards/card-blue.webp",
    srcHovered: "/blunt/cards/card-blue-hover.webp",
    colorStyle: "background-image: url(/blunt/cards/card-blue-color.png)",
    link: "https://bluntumbrellas.co.nz/products/metro-uv",
  },
  {
    id: 3,
    title: "Metro",
    price: 149,
    text: "new",
    src: "/blunt/cards/card-pink.webp",
    srcHovered: "/blunt/cards/card-pink-hover.webp",
    colorStyle: "background-image: url(/blunt/cards/card-pink-color.png)",
    link: "https://bluntumbrellas.co.nz/products/kenita-lee-metro",
  },
  {
    id: 4,
    title: "Metro",
    price: 139,
    text: "limited edition",
    src: "/blunt/cards/card-gray.webp",
    srcHovered: "/blunt/cards/card-gray-hover.webp",
    colorStyle: "background-image: url(/blunt/cards/card-gray-color.png)",
    link: "https://bluntumbrellas.co.nz/products/blunt-houndstooth-metro",
  },
  {
    id: 5,
    title: "Coupe",
    price: 139,
    src: "/blunt/cards/card-darkgray.webp",
    srcHovered: "/blunt/cards/card-darkgray-hover.webp",
    colorStyle: "background-color: #354156",
    link: "https://bluntumbrellas.co.nz/products/2020-blunt-coupe",
  },
  {
    id: 6,
    title: "Classic",
    price: 149,
    src: "/blunt/cards/card-red.webp",
    srcHovered: "/blunt/cards/card-red-hover.webp",
    colorStyle: "background-color: #ea4040",
    link: "https://bluntumbrellas.co.nz/products/2020-blunt-classic",
  },
  {
    id: 7,
    title: "Classic UV",
    price: 159,
    text: "uv protection",
    src: "/blunt/cards/card-striped.webp",
    srcHovered: "/blunt/cards/card-striped-hover.webp",
    colorStyle: "background-image: url(/blunt/cards/card-striped-color.png)",
    link: "https://bluntumbrellas.co.nz/products/classic-uv",
  },
]);

function next() {
  carousel.value.next();
}

function prev() {
  carousel.value.prev();
}
</script>

<style lang="scss" scoped>
.cards-carousel-section {
  width: 100%;
  padding: 90px 10px 90px 30px;

  &__header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 30px;
  }

  &__title {
    font-size: 54px;
    line-height: 58px;
    font-weight: 600;
  }

  &__actions {
    display: flex;
    align-items: center;
  }

  &__arrow {
    cursor: pointer;
    margin-right: 30px;
    transition: 0.3s;

    &.disabled {
      opacity: 0.4;
    }
  }

  &__button {
    border: 1px solid #cacaca;
    background: white;
    color: #262525;
    font-size: 14px;
    line-height: 18px;
    padding: 16px;
    text-align: center;
    border-radius: 5px;
    transition: 0.3s;
    font-weight: 600;
    cursor: pointer;
    margin-right: 20px;

    &:hover {
      color: #fff;
      background: #232323;
      border: 1px solid #232323;
    }
  }
}

.carousel__slide {
  margin-right: 20px;
  width: calc((100% - 60px) / 3) !important;
}

.carousel__track {
  margin-right: 30px;
}
</style>
