<script setup>
import { ChevronLeft, ChevronRight, X } from "lucide-vue-next";
import { ref } from "vue";

const props = defineProps({
  overlay: Boolean,
  handleOverlay: Function,
});

const img_src = [
  "/image-product-1.jpg",
  "/image-product-2.jpg",
  "/image-product-3.jpg",
  "/image-product-4.jpg",
];
const img_src_thumbnail = [
  "/image-product-1-thumbnail.jpg",
  "image-product-2-thumbnail.jpg",
  "image-product-3-thumbnail.jpg",
  "image-product-4-thumbnail.jpg",
];

const img_index = ref("");
let n = 0;

function handleChangeImg({ target }) {
  img_index.value = `url(${img_src[target.dataset?.index ?? 0]})`;
}

function handleRight() {
  n++;
  n > img_src.length - 1 ? (n = 0) : void 0;
  img_index.value = `url(${img_src[n ?? 0]})`;
}

function handleLeft() {
  n--;
  n < 0 ? (n = img_src.length - 1) : void 0;
  img_index.value = `url(${img_src[n ?? 0]})`;
}
</script>

<template>
  <div class="slider flex column">
    <template v-if="overlay">
      <X
        style="top: -3rem; right: 1rem; background-color: transparent"
        @click="handleOverlay"
      />
      <ChevronLeft class="i-left" style="left: -1rem" @click="handleLeft" />
      <ChevronRight class="i-right" style="right: -1rem" @click="handleRight" />
    </template>
    <div class="i transition flex center" :style="{ '--img': img_index }"></div>
    <div class="s flex">
      <div class="thn" v-for="(src_thn, i) in img_src_thumbnail">
        <img
          class="transition"
          :src="src_thn"
          :data-index="i"
          @click="handleChangeImg"
        />
      </div>
    </div>
  </div>
</template>
<style scoped>
.slider {
  width: 31.25rem;
  cursor: pointer;
  height: 38rem;
  justify-content: space-between;
  padding: 1.5%;
  position: relative;
}

.slider.overlay {
  position: fixed;
  z-index: 10;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

img {
  width: 100%;
  height: 100%;
}

.i {
  height: 80%;
  border-radius: 0.5rem;
  background-image: var(--img, url("/image-product-1.jpg"));
  background-repeat: no-repeat;
  background-size: 100% 100%;

  justify-content: space-between;

  &:hover {
    background-size: 110% 110%;
    background-position-y: -1rem;
  }

  .i-m {
    width: 100%;
    height: 100%;
    border-color: red;
  }
}

.s {
  height: 17%;
  justify-content: space-evenly;
  align-items: center;
  padding-inline: 3%;

  .thn {
    width: 18%;
    height: 80%;

    img {
      border-radius: 0.625rem;
      outline: 2px solid transparent;
      outline-offset: 3px;
      &:hover {
        outline-color: var(--orange);
        opacity: 0.7;
      }
    }
  }
}

.lucide {
  position: absolute;
  background-color: rgb(255 255 255 / 0.5);
  border-radius: 50%;
  width: 2.5rem;
  height: 2.5rem;
  top: 40%;
  stroke: #1d2025;

  &:hover {
    stroke: var(--orange);
  }
}

@media screen and (max-width: 500px) {
  #app {
    .slider {
      opacity: 0.1;
    }
  }
}
</style>
