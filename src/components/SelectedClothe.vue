<template>
  <div class="container">
    <Transition name="selected-clothe-animation" mode="out-in">
      <div :key="img">
        <img :src="img" />
        <span
          v-html="svg"
          :style="{ fill: pickedColor }"
          :key="pickedColor"
        ></span>
      </div>
    </Transition>
    <div class="color-picker">
      <div
        class="circle circle--red"
        :class="{ selectedColor: pickedColor === 'rgb(241, 61, 61)' }"
        @click="setColor('rgb(241, 61, 61)')"
      ></div>
      <div
        class="circle circle--yellow"
        :class="{ selectedColor: pickedColor === 'rgb(231, 255, 185)' }"
        @click="setColor('rgb(231, 255, 185)')"
      ></div>
      <div
        class="circle circle--green"
        :class="{ selectedColor: pickedColor === 'rgb(190, 247, 86)' }"
        @click="setColor('rgb(190, 247, 86)')"
      ></div>
      <div
        class="circle circle--blue"
        :class="{ selectedColor: pickedColor === 'rgb(86, 142, 247)' }"
        @click="setColor('rgb(86, 142, 247)')"
      ></div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
const props = defineProps({
  img: String,
  svg: String,
});
const pickedColor = ref("rgb(241, 61, 61)");

const setColor = (color) => {
  pickedColor.value = color;
};
</script>

<style scoped>
.container {
  width: clamp(15rem, 80%, 70rem);
  /* width: 700px; */
  position: relative;
  z-index: 1;
}

img {
  position: absolute;
  mix-blend-mode: multiply;

  width: 100%;
}
span {
  display: block;
}

.selectedColor {
  transform: translateY(-10%) scale(1.1);
}
.color-change-enter-active {
  animation: fade-in 0.2s linear;
}
.color-change-leave-active {
  animation: fade-in 0.2s linear reverse;
}

.selected-clothe-animation-enter-active {
  animation: scale-in 0.3s ease-in-out;
}
.selected-clothe-animation-leave-active {
  animation: scale-in 0.3s ease-in-out reverse;
}

@keyframes scale-in {
  0% {
    transform: scale(0);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

@keyframes fade-in {
  0% {
    mix-blend-mode: multiply;
    opacity: 0;
  }
  100% {
    mix-blend-mode: multiply;
    opacity: 1;
  }
}

.color-picker {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  margin-top: 1.5rem;
}

.circle {
  transition: 0.5s all ease-in;
  min-height: 2.5rem;
  min-width: 2.5rem;
  border-radius: 500%;
  border: 1px solid rgb(100, 100, 100);
  cursor: pointer;
}
.circle--red {
  background-color: rgb(241, 61, 61);
}
.circle--yellow {
  background-color: rgb(231, 255, 185);
}
.circle--green {
  background-color: rgb(190, 247, 86);
}
.circle--blue {
  background-color: rgb(86, 142, 247);
}
</style>
