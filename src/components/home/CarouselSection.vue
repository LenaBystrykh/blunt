<template>
  <div class="carousel-section">
    <Carousel
      :autoplay="5000"
      :wrap-around="true"
      v-model="currentSlide"
      :items-to-show="1"
    >
      <Slide v-for="slide in carousel" :key="slide.id">
        <CarouselSlide :slide="slide" />
      </Slide>

      <template #addons>
        <Pagination />
      </template>
    </Carousel>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination } from "vue3-carousel";
import CarouselSlide from "@/components/home/CarouselSlide.vue";

const carousel = reactive([
  {
    id: 1,
    title: "Kenita-Lee",
    text: "We're proud to showcase our latest limited edition collaboration with First Nations artist, Kenita-Lee McCartney. The captivating design weaves in ancestral narratives of unity, unwavering strength, and guidance.",
    src: "/blunt/carousel/pink.webp",
    color: "#d5477e",
  },
  {
    id: 2,
    title: "Leopard",
    text: "Go wild for leopard with our latest limited edition, featuring the iconic leopard print in classic tones of camel and black.",
    src: "/blunt/carousel/beige.webp",
    color: "#ca9f6a",
  },
]);
</script>

<style lang="scss">
.carousel-section {
  width: 100%;
  max-height: 840px;
}

.carousel__pagination {
  position: absolute;
  bottom: 50px;
  left: 50%;
  width: 50%;
}

.carousel__pagination-button::after {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  margin: 0 15px;
  background-color: rgba(255, 255, 255, 0.2);
}

.carousel__pagination-button:hover::after,
.carousel__pagination-button--active::after {
  background-color: white;
}
</style>
