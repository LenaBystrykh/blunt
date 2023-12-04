<template>
  <div class="card" @click="toPage">
    <div class="card__header">
      <div class="card__header-left">
        <h3 class="card__title">{{ card.title }}</h3>
        <p class="card__price">${{ card.price }}</p>
      </div>
      <div class="card__header-right">
        <p class="card__text">{{ card.text ? card.text : "" }}</p>
        <span class="card__color" :style="card.colorStyle"></span>
      </div>
    </div>
    <div
      class="card__image"
      @mouseover="isHovered = true"
      @mouseleave="isHovered = false"
    >
      <img :class="{ visible: isHovered }" :src="card.srcHovered" />
      <img :class="{ visible: !isHovered }" :src="card.src" />
    </div>
    <button class="card__button">Add to Bag</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isHovered = ref(false);

const props = defineProps({
  card: Object,
});

function toPage() {
  window.open(props.card.link, "_blank");
}
</script>

<style lang="scss">
.card {
  background: #f5f5f5;
  overflow: hidden;
  padding: 20px;
  cursor: grab;

  &__header {
    width: 100%;
    display: flex;
    align-items: flex-start;
    justify-content: space-between;

    &-right {
      display: flex;
      align-items: center;
      margin-left: 30px;
    }
  }

  &__title {
    font-size: 28px;
    font-weight: 600;
  }

  &__price {
    font-size: 18px;
    line-height: 24px;
    letter-spacing: 0;
    margin-top: 10px;
    text-align: left;
  }

  &__text {
    text-align: right;
    font-weight: 500;
    font-size: 10px;
    line-height: 12px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-right: 10px;
  }

  &__color {
    display: block;
    height: 20px;
    width: 20px;
    border-radius: 50%;
    position: relative;
    background-size: 100% 100%;
  }

  &__image {
    width: 100%;
    height: 100%;
    position: relative;
    cursor: pointer;

    img {
      width: 100%;
      opacity: 0;
      transition: 0.3s;

      &.visible {
        position: absolute;
        top: 0;
        left: 0;
        opacity: 1;
      }
    }
  }

  &__button {
    width: 100%;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: white;
    color: #262525;
    font-size: 14px;
    line-height: 18px;
    border-radius: 5px;
    outline: none;
    border: none;
    cursor: pointer;
    transition: 0.3s;

    &:hover {
      color: white;
      background: #232323;
    }
  }
}
</style>
