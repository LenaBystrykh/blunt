<template>
  <div class="about">
    <canvas width="500" height="500" ref="canvas" />
    <button @click="changeUmbrellaImage">следующая!</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const url = ref("/3dmotion/Blunt_HPFinal0010_0010.jpg");
const canvas = ref();
let imgNumber = 10;

function changeUmbrellaImage() {
  url.value = `/3dmotion/Blunt_HPFinal00${imgNumber}_00${imgNumber}.jpg`;
  const context = canvas.value.getContext("2d");
  context.clearRect(0, 0, canvas.value.width, canvas.value.height);
  const image = new Image();
  image.src = url.value;
  image.onload = function () {
    context.drawImage(image, 0, 0);
  };
  imgNumber++;
}
</script>
