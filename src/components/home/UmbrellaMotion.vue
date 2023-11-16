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
          <div class="umbrella__info">
            <div class="umbrella__option">
              <div class="umbrella__option-area"></div>
              <div class="umbrella__option-button" @click="toggleButton(1)">
                <div
                  class="umbrella__option-plus-v"
                  :class="{ selected: buttonNum === 1 }"
                ></div>
                <div class="umbrella__option-plus-h"></div>
              </div>
            </div>
            <div class="umbrella__option">
              <div class="umbrella__option-area"></div>
              <div class="umbrella__option-button" @click="toggleButton(2)">
                <div
                  class="umbrella__option-plus-v"
                  :class="{ selected: buttonNum === 2 }"
                ></div>
                <div class="umbrella__option-plus-h"></div>
              </div>
            </div>
            <div class="umbrella__option">
              <div class="umbrella__option-area"></div>
              <div class="umbrella__option-button" @click="toggleButton(3)">
                <div
                  class="umbrella__option-plus-v"
                  :class="{ selected: buttonNum === 3 }"
                ></div>
                <div class="umbrella__option-plus-h"></div>
              </div>
            </div>
            <div class="umbrella__description">
              <h2>The BLUNT difference</h2>
              <p>
                We believe there’s strength in simplicity – using materials
                smarter and making components work harder means your BLUNT is
                meticulously designed and refined to withstand whatever life
                throws at you.
              </p>
            </div>
            <div class="umbrella__popups">
              <div
                class="umbrella__popup"
                :class="{ selected: buttonNum === 1 }"
              >
                <div class="umbrella__popup-image">
                  <img src="@/assets/images/popup-tip.webp" />
                </div>
                <h3>BLUNT Tip</h3>
                <p>
                  Each patented BLUNT tip acts like a mini umbrella, opening
                  under full force to evenly distribute tension from the frame
                  to the canopy edge.
                </p>
              </div>
              <div
                class="umbrella__popup"
                :class="{ selected: buttonNum === 2 }"
              >
                <div class="umbrella__popup-image">
                  <img src="@/assets/images/popup-frame.webp" />
                </div>
                <h3>Frame</h3>
                <p>
                  The BLUNT umbrella frame exhibits a unique strut mechanism,
                  pushing maximum radial force out towards the ribs resulting in
                  our highly tensioned canopy.
                </p>
              </div>
              <div
                class="umbrella__popup"
                :class="{ selected: buttonNum === 3 }"
              >
                <div class="umbrella__popup-image">
                  <img src="@/assets/images/popup-canopy.webp" />
                </div>
                <h3>Canopy</h3>
                <p>
                  Our iconic canopy shape is the result of our patented BLUNT
                  tips providing a taut contour for ultimate performance and our
                  distinctive and iconic shape.
                </p>
              </div>
            </div>
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
const buttonNum = ref(0);

function changeUmbrellaImage(value) {
  // 0.53 because durations summ = 26, before umbrella 13/26 = 0.5, slightly after that movement begins
  if (Math.abs(value) > 0.53) {
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

function toggleButton(num) {
  if (buttonNum.value === num) {
    buttonNum.value = 0;
  } else {
    buttonNum.value = num;
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
    })
    .to(".umbrella__info", {
      opacity: 1,
      ease: "none",
      duration: 3,
    });
});
</script>

<style lang="scss">
.umbrella {
  width: 100%;
  height: 300vh;
  background-color: #efefef;
  position: relative;
  overflow: visible;
  padding: 0 0 200vh 0;
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

  &__info {
    width: 100%;
    height: 100vh;
    position: absolute;
    opacity: 0;
  }

  &__description {
    max-width: 350px;
    padding-left: 40px;
    padding-top: 70px;
    text-align: left;

    h2 {
      font-size: 54px;
      line-height: 58px;
      font-weight: 600;
      margin-bottom: 20px;
    }

    p {
      font-size: 15px;
      font-weight: 500;
      letter-spacing: 0.02em;
    }
  }

  &__option {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 68px;
    height: 68px;

    &:nth-of-type(1) {
      top: 5%;
      left: 70%;
    }

    &:nth-of-type(2) {
      top: 26%;
      left: 45%;
    }

    &:nth-of-type(3) {
      top: 66%;
      left: 34%;
    }
  }

  &__option-button {
    width: 100%;
    height: 100%;
    position: relative;
    border-radius: 50%;
    background-color: #484646;
    cursor: pointer;
  }

  &__option-plus-v {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 2px;
    height: 32px;
    background-color: white;
    transform: translate(-50%, -50%);
    opacity: 1;
    transition: 0.3s;

    &.selected {
      opacity: 0;
    }
  }

  &__option-plus-h {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 32px;
    height: 2px;
    background-color: white;
    transform: translate(-50%, -50%);
  }

  &__option-area {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(163, 163, 163, 0.15);
    border-radius: 50%;
    animation: sparkle 1.5s linear infinite;
    -webkit-animation: sparkle 1.5s linear infinite;
  }

  &__popup {
    max-width: 176px;
    z-index: 19;
    text-align: left;
    position: absolute;
    opacity: 0;
    transform: translateY(15px);
    transition: 0.5s;

    &.selected {
      opacity: 1;
      transform: translateY(0);
    }

    &:nth-of-type(1) {
      top: 4%;
      left: 78%;
    }

    &:nth-of-type(2) {
      top: 35%;
      left: 70%;
    }

    &:nth-of-type(3) {
      top: 50%;
      left: 9%;
    }

    &-image {
      border-radius: 8px;
      overflow: hidden;

      img {
        width: 100%;
      }
    }

    h3 {
      font-size: 22px;
      line-height: 28px;
      font-weight: 600;
      margin: 35px 0 15px 0;
    }

    p {
      font-size: 13px;
      line-height: 17px;
      letter-spacing: 0;
      font-weight: 500;
    }
  }
}

@keyframes sparkle {
  0% {
    scale: 1;
    opacity: 1;
  }
  80% {
    scale: 1.8;
    opacity: 1;
  }
  100% {
    scale: 1.8;
    opacity: 0;
  }
}
</style>
