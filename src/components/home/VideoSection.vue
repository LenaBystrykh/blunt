<template>
  <div class="video-section">
    <video
      autoplay
      muted
      loop
      src="https://cdn.shopify.com/videos/c/vp/9ad8234d6e6342bb8851940db3c8f12c/9ad8234d6e6342bb8851940db3c8f12c.HD-1080p-7.2Mbps-16721862.mp4"
    />
    <div class="video-section__content">
      <div class="video-section__title" id="engineering">
        <div>E</div>
        <div>n</div>
        <div>g</div>
        <div>i</div>
        <div>n</div>
        <div>e</div>
        <div>e</div>
        <div>r</div>
        <div>i</div>
        <div>n</div>
        <div>g</div>
      </div>
      <div class="video-section__extra">
        <p class="video-section__info">
          Intelligently designed products to equip
        </p>
        <p class="video-section__info">you for your well-considered life.</p>
        <div class="video-section__actions">
          <button class="video-section__button video-section__button--white">
            Shop All
          </button>
          <button
            class="video-section__button video-section__button--transparent"
          >
            Explore Umbrellas
          </button>
        </div>
      </div>
      <div class="video-section__title" id="joy">
        <div>J</div>
        <div>o</div>
        <div>y</div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.video-section {
  width: 100%;
  height: 100vh;
  position: relative;

  video {
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 1;
  }

  &__content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: 70% 30%;
    grid-template-rows: 50% 50%;
    z-index: 2;
  }

  &__title {
    color: white;
    font-size: 140px;
    font-weight: 600;
    display: flex;
  }

  &__extra {
    grid-row: 2;
    grid-column: 1;
    text-align: left;
    color: white;
    align-self: flex-end;
    margin-bottom: 50px;
    margin-left: 50px;
    height: 120px;
    overflow: hidden;

    .video-section__info {
      transform: translateY(100%);
      opacity: 0;
      animation: infoAppearance 0.5s linear forwards;
    }

    p:nth-child(1) {
      animation-delay: 2.2s;
    }
    p:nth-child(2) {
      animation-delay: 2.35s;
    }

    .video-section__actions {
      button:nth-child(1) {
        animation-delay: 2.5s;
      }
      button:nth-child(2) {
        animation-delay: 2.6s;
      }
    }
  }

  #engineering {
    grid-row: 1;
    grid-column: 1;
    padding: 80px 0 50px 30px;
    text-align: left;
    height: 300px;
    overflow: hidden;

    div {
      transform: translateY(-400px);
      animation: bouncingDown 1.5s linear forwards;
    }

    div:nth-child(1) {
      animation-delay: 0.05s;
    }
    div:nth-child(2) {
      animation-delay: 0.1s;
    }
    div:nth-child(3) {
      animation-delay: 0.15s;
    }
    div:nth-child(4) {
      animation-delay: 0.2s;
    }
    div:nth-child(5) {
      animation-delay: 0.25s;
    }
    div:nth-child(6) {
      animation-delay: 0.3s;
    }
    div:nth-child(7) {
      animation-delay: 0.35s;
    }
    div:nth-child(8) {
      animation-delay: 0.4s;
    }
    div:nth-child(9) {
      animation-delay: 0.45s;
    }
    div:nth-child(10) {
      animation-delay: 0.5s;
    }
    div:nth-child(11) {
      animation-delay: 0.55s;
    }
  }

  #joy {
    grid-row: 2;
    grid-column: 2;
    text-align: right;
    padding-right: 50px;
    padding-bottom: 70px;
    align-self: flex-end;
    justify-self: flex-end;
    height: 240px;
    overflow: hidden;

    div {
      transform: translateY(400px);
      animation: bouncingUp 1.5s linear forwards;
    }

    div:nth-child(1) {
      animation-delay: 1.2s;
    }
    div:nth-child(2) {
      animation-delay: 1.25s;
    }
    div:nth-child(3) {
      animation-delay: 1.3s;
    }
  }

  &__button {
    width: 214px;
    height: 50px;
    padding: 16px;
    border-radius: 5px;
    outline: none;
    border: none;
    margin: 30px 20px 0 0;
    transition: 0.3s;
    cursor: pointer;
    font-size: 14px;
    font-weight: 600;
    animation: infoAppearance 0.8s linear forwards;
    transform: translateY(100%);
    opacity: 0;

    &--white {
      background: white;
      color: #262525;
    }

    &--transparent {
      background: rgba(255, 255, 255, 0.2);
      color: white;
    }

    &:hover {
      background: #262525;
      color: white;
    }
  }
}

@keyframes bouncingDown {
  0% {
    transform: translateY(-400px);
  }
  60% {
    transform: translateY(20px);
  }
  100% {
    transform: translateY(0px);
  }
}

@keyframes bouncingUp {
  0% {
    transform: translateY(400px);
  }
  60% {
    transform: translateY(-20px);
  }
  100% {
    transform: translateY(0px);
  }
}

@keyframes infoAppearance {
  0% {
    transform: translateY(100%);
    opacity: 0;
  }
  100% {
    transform: translateY(0px);
    opacity: 1;
  }
}
</style>
