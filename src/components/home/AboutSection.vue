<template>
  <div class="about-section">
    <div class="about-section__header">
      <p class="about-section__title">
        BLUNT is a human-centred product design company.
      </p>
      <button class="about-section__button">About Us</button>
    </div>
    <div class="about-section__content">
      <div class="about-section__card">
        <EngineeringIcon class="card__icon" />
        <h3 class="card__title">Engineering Excellence</h3>
        <p class="card__text">
          We look beyond the past and present to create innovative products,
          unbound by convention and built to withstand all that life throws our
          way.
        </p>
      </div>
      <div class="about-section__card">
        <DesignIcon class="card__icon" />
        <h3 class="card__title">Iconic Design</h3>
        <p class="card__text">
          A unique fusion of form and function; harmonising engineering with
          artistry, resulting in products that are both iconic and distinctive.
        </p>
      </div>
      <div class="about-section__card">
        <SustainableIcon class="card__icon" />
        <h3 class="card__title">Built to last</h3>
        <p class="card__text">
          Designed to stand the test of time and made for generations to come.
          Our products are modular, repairable and future-proofed.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import DesignIcon from "../svg/DesignIcon.vue";
import EngineeringIcon from "../svg/EngineeringIcon.vue";
import SustainableIcon from "../svg/SustainableIcon.vue";
</script>

<style lang="scss">
.about-section {
  position: relative;
  padding: 100px 50px;
  background-color: #f6f6f6;
  z-index: 10;

  &__header {
    margin-bottom: 100px;
    display: flex;
    justify-content: space-between;
  }

  &__title {
    text-align: left;
    max-width: 440px;
    font-size: 34px;
    font-weight: 600;
  }

  &__button {
    width: 214px;
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

  &__content {
    display: flex;
  }

  &__card {
    flex: 1;
    text-align: left;

    .card {
      &__icon {
        margin-bottom: 50px;
      }

      &__title {
        margin-bottom: 20px;
        font-size: 22px;
        font-weight: 600;
      }

      &__text {
        max-width: 345px;
        font-size: 15px;
        font-weight: 500;
      }
    }
  }
}
</style>
