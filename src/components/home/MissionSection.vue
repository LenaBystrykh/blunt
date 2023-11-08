<template>
  <div class="mission-section">
    <div class="mission-section__content">
      <h2 class="mission-section__title">
        Designed for today. Made for tomorrow.
      </h2>
      <p class="mission-section__text">
        Our vision is to create products better than those that came before.
        Products built to last that are modular and repairable. Products that
        will be with you for life if they are cared for, trusted and respected,
        and in return will provide you with joy and confidence during life’s
        vulnerable moments.
      </p>
    </div>
    <img class="mission-section__img" src="@/assets/images/homepage.jpg" />
  </div>
</template>

<style lang="scss">
.mission-section {
  display: flex;
  background-color: #f1f1f1;
  width: 100%;
  height: 100vh;
  padding: 93px 20px 20px 50px;

  &__content {
    flex: 1;
    text-align: left;

    .mission-section__title {
      display: block;
      width: 560px;
      font-size: 95px;
      line-height: 90px;
      font-weight: 600;
      margin-bottom: 50px;
    }

    .mission-section__text {
      display: block;
      width: 400px;
      font-size: 18px;
      font-weight: 500;
    }
  }

  &__img {
    max-width: 100%;
    max-height: 100%;
    border-radius: 8px;
  }
}
</style>
