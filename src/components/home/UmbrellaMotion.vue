<template>
  <div class="umbrella">
    <div class="umbrella__animation">
      <div class="umbrella__outline-section">
        <div class="umbrella__animation-content">
          <div class="umbrella__animation-image">
            <div class="umbrella__outline" ref="umbrellasvg">
              <img src="@/assets/images/outline.svg" />
            </div>
          </div>
          <div class="umbrella__animation-text">
            <div class="umbrella__text" ref="text">
              <h2>Beautiful umbrellas, built to last.</h2>
              <br /><br />
              <h2>
                Providing joy and confidence in life's vulnerable moments.
              </h2>
            </div>
          </div>
        </div>
      </div>
      <div class="umbrella__filling">
        <div class="umbrella__filling-content">
          <div class="umbrella__filling-image">
            <img :src="url" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

let imgNumber = 10;
let prevProgress = 0;
const umbrellasvg = ref();
const url = ref("/3dmotion/Blunt_HPFinal0010_0010.jpg");

function changeUmbrellaImage(value) {
  // 0.57 because durations summ = 23, umbrella movement takes 10/23, 13/23 = 0.57, after that movement begins
  if (Math.abs(value) > 0.57) {
    if (value === 1) {
      url.value = "/3dmotion/Blunt_HPFinal0152_0152.jpg";
    }
    if (prevProgress < value && imgNumber < 152) {
      // scroll down
      imgNumber++;
      prevProgress = value;
    } else if (prevProgress > value && imgNumber > 10) {
      // scroll up
      imgNumber--;
      prevProgress = value;
    }
    if (imgNumber < 100) {
      url.value = `/3dmotion/Blunt_HPFinal00${imgNumber}_00${imgNumber}.jpg`;
    } else {
      url.value = `/3dmotion/Blunt_HPFinal0${imgNumber}_0${imgNumber}.jpg`;
    }
  } else {
    url.value = "/3dmotion/Blunt_HPFinal0010_0010.jpg";
  }
}

onMounted(() => {
  let tl = gsap.timeline({
    scrollTrigger: {
      trigger: ".umbrella",
      start: "100px 100px",
      end: "bottom top",
      scrub: 2,
      pin: true,
      onUpdate: (self) => changeUmbrellaImage(self.progress),
    },
  });
  tl.to(".umbrella__text", {
    translateY: "-100%",
    ease: "none",
    duration: 6,
  })
    .to(".umbrella__outline", {
      scale: 1,
      ease: "none",
      duration: 2,
    })
    .to(".umbrella__filling", {
      clipPath: "inset(0% 0% 0%)",
      ease: "none",
      duration: 5,
    })
    .to(".umbrella__filling-image", {
      ease: "none",
      duration: 10,
    });
});
</script>

<style lang="scss">
.umbrella {
  width: 100%;
  height: 400vh;
  background-color: #efefef;
  position: relative;
  overflow: visible;
  padding: 0 0 250vh 0;
  margin: 0;
  display: block;

  &__animation {
    translate: none;
    rotate: none;
    scale: none;
    left: 0px;
    top: 0;
    margin: 0px;
    max-width: 100%;
    width: 100%;
    max-height: 100vh;
    height: 100vh;
    padding: 0px;
    box-sizing: border-box;
    position: fixed;
    transform: translate(0px, 0px);
    background: #efefef;
    position: relative;
    overflow-x: hidden;
  }

  &__outline-section {
    position: absolute;
    z-index: 4;
  }

  &__animation-content {
    position: relative;
    height: 100vh;
    width: 100vw;
    overflow: hidden;
  }

  &__animation-image {
    min-height: 100vh;
    min-width: 100vw;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate3d(-50%, -50%, 0);
  }

  &__outline {
    transform: scale(1.3, 1.3);
    transform-origin: 50% 0%;

    img {
      max-width: none;
      width: 100%;
      display: block;
    }
  }

  &__animation-text {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 9;
    mask-image: linear-gradient(
      to bottom,
      transparent 0%,
      black 20%,
      black 80%,
      transparent 100%
    );
    -webkit-mask-image: linear-gradient(
      to bottom,
      transparent 0%,
      black 20%,
      black 80%,
      transparent 100%
    );
  }

  &__text {
    position: relative;
    max-width: 1085px;
    margin: auto;
    text-align: center;
    display: flex;
    gap: 90px;
    flex-direction: column;
    height: 100%;
    align-items: center;
    justify-content: center;
    transform: translate(0%, 100%);

    h2 {
      font-size: 95px;
      font-weight: 600;
      line-height: 0.95em;
    }
  }

  &__filling {
    position: relative;
    clip-path: inset(100% 0% 0%);
    z-index: 9;

    &-content {
      position: relative;
      height: 100vh;
      width: 100vw;
      overflow: hidden;
    }

    &-image {
      min-height: 100vh;
      min-width: 100vw;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate3d(-50%, -50%, 0);

      img {
        width: 100%;
      }
    }
  }
}
</style>
