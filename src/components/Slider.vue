<script setup>
import { ChevronLeft, ChevronRight, X } from "lucide-vue-next";

const props = defineProps({
  overlay: Boolean,
  handleLeft: Function,
  handleRight: Function,
  handleCancel: Function,
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
</script>

<template>
  <div class="slider flex column">
    <template v-if="overlay">
      <X style="top: -4rem; right: 0" @click="handleCancel" />
      <ChevronLeft class="i-left" style="left: -1rem" @click="handleLeft" />
      <ChevronRight class="i-right" style="right: -1rem" @click="handleRight" />
    </template>
    <div class="i transition flex center"></div>
    <div class="s flex">
      <div class="thn" v-for="(src_thn, i) in img_src_thumbnail">
        <img class="transition" :src="src_thn" />
      </div>
    </div>
  </div>
</template>
<style scoped>
.slider {
  width: 31.25rem;
  cursor: pointer;
  /* replace with relative values */
  height: 38rem;
  justify-content: space-between;
  padding: 1.5%;
  position: relative;
}

img {
  width: 100%;
  height: 100%;
}

.i {
  height: 80%;
  border-radius: 0.5rem;
  background-image: url("/image-product-1.jpg");
  background-repeat: no-repeat;
  background-size: 100% 100%;

  justify-content: space-between;
  /* background-position: 480px; */

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
  background-color: rgb(255 255 255 / 0.8);
  border-radius: 50%;
  width: 40px;
  height: 40px;
  top: 40%;

  &:hover {
    stroke: var(--orange);
  }
}
</style>
