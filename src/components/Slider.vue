<script setup>
// import { CircleChevronLeft, CircleChevronRight } from "lucide-vue-next";
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
  <div class="slider bd flex column ">
    <div class="i transition ">
      <!-- <CircleChevronLeft />
      <CircleChevronRight /> -->
    </div>
    <div class="s flex">
      <div class="thn" v-for="src_thn in img_src_thumbnail">
        <img class="transition" :src="src_thn" />
      </div>
    </div>
  </div>
</template>
<style scoped>
.slider {
  width: 31.25rem;
  /* replace with relative values */
  height: 40rem;
  justify-content: space-between;
  padding: 1.5%;
}

img {
  width: 100%;
  height: 100%;
  /* border-radius: inherit; */
}

.i {
  height: 80%;
  border-radius: 0.5rem;
  background-image: url("/image-product-1.jpg");
  background-repeat: no-repeat;
  background-size: 100% 100%;
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
  /* border-color: red; */
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
        opacity: .7;
      }
    }
  }
}
</style>
