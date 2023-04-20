<template>
  <div class="clothes">
    <selected-clothe
      :img="clothes[currentSection][currentProduct].img"
      :svg="clothes[currentSection][currentProduct].svg"
    ></selected-clothe>

    <div class="clothes-selector">
      <div class="category-selector">
        <span
          @click="setSection('shirts', '0')"
          :class="{ 'category-selected': currentSection === 'shirts' }"
          >T-SHIRTS</span
        >
        <span
          @click="setSection('shoes', '0')"
          :class="{ 'category-selected': currentSection === 'shoes' }"
          >SHOES</span
        >
      </div>
      <ul v-auto-animate>
        <clothe-item
          v-for="clothe in clothes[currentSection]"
          :key="clothe.id"
          :id="clothe.id"
          :img="clothe.img"
          :currentId="currentProduct"
          @set-image="setCurrentClothe"
        ></clothe-item>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import SelectedClothe from "./components/SelectedClothe.vue";
import ClotheItem from "./components/ClotheItem.vue";
const clothes = {
  shirts: [
    {
      id: "0",
      img: "products/shirt-1.png",
      svg: '<svg id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 525 525"><polygon class="cls-1" points="216.5 215.5 204.09 215.5 192.5 218.5 182.5 221.5 157.5 228.5 143.5 229.5 139.5 231.5 132.5 234.5 109.5 237.5 103.5 242.5 95.5 249.5 85 259 76 262.5 73 280 65 307 54 324 56 331 62 335 74 343 88 346 110.17 346 122 343 120 354 120 381 121 403 121 420 121 433 119 454 113 468 114 483 117 487 115 495 114 510 108.87 525 372.09 525 382 518 385 509 380 500 375 495 383 488 387 475 388 450 388 421.65 387 402 389 389 387 355 397 358 420 358 441 351 446 347 446 325.39 448 307 445 278 442 270 422 253 405 246 389 244 367 235 357 234 332 223 317 218 316 220 317 224 322 227 327 229 325 236 320 243 312 247 302 251 280 254 249 252 230 247 211 235 204 223 207 219 216.5 215.5"/></svg>',
    },
    {
      id: "1",
      img: "products/shirt-2.png",
      svg: '<svg id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 525 525"><path class="cls-1" d="M191.5,169.5l-21,9L137,189l-26,7-12,6L82,223l-8,26L64,275,52,293l-2,3,5,5,27,8,20,4h12.48l6.27-4L119,325l-1,18-2,20v27l-3,9-4,9-2,12v7l10,5,9,1,13,4,9,6,19,14,16,7,8.5,3.63L190,472l-10,4-12-3-14-5-8-4-1,4,2,5-5,2-2,8-2,6,2,4,45,15,38,6,47,6,22,2,36,1,43-3,8-5,2-2-4-8,2-8-2-10-8-10-2-18-3-18-3-21-3-18-9-2-4,12-4,6h-8l-3-5,2-21-8,4h-8l-1-3,4-6,4-7,2-13,3-11,17-19,6-10,13-8,5-9V298l-2-5-1-3,4-8,24-3,17-3,8-5v-4.3l-5-7.7-2-15-3-6-1-35-1-14-8-8-12-7-14-2-50-9-21-4-1,2,4,5-2,6-7,6s-11,7-12,7-11,3-11,3H248l-17-1-19-3-16-6-2-5,6-4-3-1Z"/></svg>',
    },
    {
      id: "2",
      img: "products/shirt-3.png",
      svg: '<svg id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 525 525"><path class="cls-1" d="M225.5,245.5l-8,2A15.52,15.52,0,0,0,215,251c-1.13,2.18-1.21,3.64-2,7-.65,2.76-.69,2.17-2,7-.5,1.83-1.22,4.58-2,8l-5,20-4,13-8,23-5,14-4,13v3.43L177,370l9,9,2,4,1,3-3,5,1,2-5,2-6,8-3,8-4,12v3l14,2,39,4,32,2,42,2,22,2,26,1h3.7l2.3-5-2-2,3-2,1-4,1-3v-3l-2-4,4-10,1-5a10.07,10.07,0,0,0,1-3v-3.35l1-1.65,1-4,1-3,1-4-1-6v-6l-1-2V348h8l19-1,18-1,5.65-3.75L408,336l-3-7-1-9-3-10-2-10-3-10-4-14v-8l-2-1-2.65-4.5L384,257l-4-4-11-4-25-6-13-4-8-4h-1.78L318,239v3l-7,5-10,4-3,1-18,18-7,7-1,2-1,1a5,5,0,0,1-6,0c-.33-.67-.67-1.33-1-2l-5-6-8-12-3-6-10-4-1-4-7-2Z"/><path class="cls-1" d="M177,262l-6,6h0q-2,4.88-4,10-1.56,4-3,8l-3,7-2,7-1,7-5,12-7,8v9.09l5,3.91h10.43l7.57,4.43,1-2.43,1-7,4-22,5-25,3-13,4-17.3v-3.27Z"/><polygon class="cls-1" points="250 254 253 260 262.5 272.96 265 276 270.74 276 279 269 292 255 294 253 277.26 254.44 262.5 254.44 254.04 254.44 250 254"/></svg>',
    },
  ],
  shoes: [
    {
      id: "0",
      img: "products/shoes-1.png",
      svg: '<svg id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 525 525"><path class="cls-1" d="M158.2,310.06,141.73,316l-8,4.64L127.16,327l-1.9,3.38,4.23,2.53,12.24,2.32,13.73,1.06,49.83,1.06L257.66,335l23.65-2.74,35.47-8.55,24.92-6,23-4.23,24.07-3.37,17.32-1.69,15-3.17,12.46-4.65,1.9-2.74V295.7s-.85-6.34,0-7,0-6.76,0-6.76l.37-6.33s-2.48-6.34-2.7-7-1.68-4.74-2.11-6.17-1.26-4-1.26-4a34,34,0,0,0-7.39,1.91c-3.8,1.47-17.53,7.17-17.53,7.17l-34.21,12.46-29.35,11.19-23.44,9.08L295,309.63l-26.82,9.72-5.71,2.11-4.63-4.65-8.66-9.08-12.67-9.81-8.66-5.39a52.45,52.45,0,0,0-9.29-1.69c-4-.21-15,1.27-15,1.27l-11,3.38-9.08,2.43L178.05,302,165,308.16Z"/><polygon class="cls-2" points="170.03 81.59 175.52 79.9 182.91 78 189.66 76.94 197.06 76.94 207.4 78.21 219.23 81.59 226.83 84.97 234.43 89.19 240.34 94.89 249.63 106.5 253.86 115.58 253.86 131 253.86 150.42 255.54 167.32 260.61 183.79 272.65 205.53 281.94 220.95 288.27 236.15 288.27 228.76 288.27 220.53 287.22 210.18 285.53 201.31 284.05 193.08 282.36 181.25 280.54 169.22 278.77 152.75 275.6 137.97 271.59 118.96 269.48 107.14 265.89 95.95 259.77 82.64 254.49 75.89 242.24 66.81 231.05 62.59 222.18 62.59 208.46 60.9 199.38 62.16 192.2 67.23 182.06 73.35 170.03 81.59"/></svg>',
    },
    {
      id: "1",
      img: "products/shoes-2.png",
      svg: '<svg id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 525 525"><path d="M157,400h4.64l7.36-6,7-9,7-6,9-15,12-18,12-14,8-5,8-2,3-4,1-3v-8.4l-3-6.6-1-5,1-7,5-6,14-10,14.62-12.5L275,252l11-29,9-29,6-22,7-24,6-19,5-7,9-2-11-7h-5.83L302,105l-4-6h-3.51L284,92l-8-4-7,1-5,4-1.5,6.25L266,109l5,15,3,7-3,15-5,9-8,6-15.5,6.2L223,175l-10,7-4,7v5l7-2,3-4h6l4-7h8l1,3,2,4v3a22.69,22.69,0,0,1-1,4l-4,3h-5l-2,4-3,3h-4l-3-1-6,1,4,19h6l1,2,1,3-1,5-3,2-5,1v3l5,2,2.27,2,.73,2v3l-1,1-1,1-1,1h-3a22.69,22.69,0,0,1-4-1h-1l-1,1-3,4,1,4h7l1.18,2.5L216,269l-5,4,3,4,1,4-1,3-3,2h-4l-1,5,3,1,1,2v2l-1,6-7,4v4l3,2v4l-1,4-2,2-7-1-3,13-3,8-6,6-3,6-4,11-6,10-8,13-4,8Z"/><polygon class="cls-1" points="288 156 267 213 262.5 223.35 258 230 253 231 250 229 245 223 242.5 219.69 242.5 225.38 242.5 232.5 244 238 246.07 244 249 248 253 250 259.09 250 262.5 247.76 268 241 272 231 283 199 291 170 288 156"/></svg>',
    },
    // {
    //   id: "11",
    //   img: "products/shoes-2.png",
    // },
    // {
    //   id: "22",
    //   img: "products/shoes-3.png",
    // },
  ],
};

const currentSection = ref("shirts");
const currentProduct = ref("0");

const setCurrentClothe = (id) => {
  currentProduct.value = id;
};

const setSection = (section, defaultClothe) => {
  console.log(section, defaultClothe);
  currentSection.value = section;
  currentProduct.value = defaultClothe;
};

console.log(clothes[currentSection.value]);
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@400;500;600&display=swap");
*,
*::after,
*::before {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html {
  font-family: "Raleway", sans-serif;
}

.clothes {
  max-width: 70%;
  /* background-color: red; */
  margin: 0 auto;
  gap: 2.5rem;
  padding: 2.5rem;
  background-color: rgb(224, 224, 224);
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  /* justify-items: center; */
}

ul {
  display: flex;
  flex-direction: column;
  align-items: start;
  justify-content: start;
  gap: 1rem;
}
.selected-clothe-animation-enter-active {
  animation: scale-in 1s ease-in-out;
}

@keyframes scale-in {
  0% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}

.clothes-selector {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
}

.category-selector {
  display: flex;
  justify-content: flex-start;
  gap: 1.5rem;
  background-color: rgb(243, 231, 231);
}
.category-selected {
  background-color: rgba(179, 176, 176, 0.342);
}
.category-selector span {
  cursor: pointer;
  font-size: 1.6rem;
  padding: 1rem;
  transition: 0.3s all linear;
}

@media screen and (max-width: 64.125em) {
  .category-selector {
    /* justify-content: center; */
  }
  .clothes {
    max-width: 90%;
  }

  ul {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }
}

@media screen and (max-width: 35.125em) {
  .clothes {
    padding: 2rem 0;
  }
}

@media screen and (max-width: 50em) {
  .clothes {
    justify-items: center;
  }
}
</style>
