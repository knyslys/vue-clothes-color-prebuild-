<template>
  <li>
    <div :class="{ selected: id === currentId }" class="img-wrapper">
      <img :src="img" @click="$emit('set-image', id)" />
    </div>
  </li>
</template>

<script setup>
import { ref } from "vue";
const props = defineProps(["id", "img", "currentId"]);
// const selectedId = ref(props.currentId.value);
defineEmits(["set-image"]);
console.log(props.currentId.value);
</script>

<style scoped>
li {
  list-style: none;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
.img-wrapper {
  display: inline-block;
  /* max-width: 20%; */
  width: clamp(5rem, 10%, 20rem);
  position: relative;
  border-radius: 500%;
  overflow: hidden;
}

.selected::after {
  background-color: rgba(216, 180, 180, 0.514);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: "";
  transition: 1s all linear;
}

img {
  display: block;
  /* width: clamp(2.5rem, 15vw, 30rem); */

  max-height: 5rem;
  cursor: pointer;
  display: block;
  /* object-fit: center; */
}

@media screen and (max-width: 35.125em) {
  img {
    max-height: 3rem;
  }
}
</style>
