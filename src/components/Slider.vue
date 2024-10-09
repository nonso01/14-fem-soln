<script setup>
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
  <div class="slider flex column bd">
    <div class="i  bd">
      <div class="" v-for="src in img_src"><img :src="src" /></div>
    </div>
    <div class="s flex bd">
      <div class="thn bd" v-for="src_thn in img_src_thumbnail"><img :src="src_thn" /></div>
    </div>
  </div>
</template>
<style scoped>
.slider {
  width: 31.25rem;
  /* replace with relative values */
  height: 33.75rem;
  justify-content: space-between;
  padding: 1.5%;
}

img {
  width: 100%;
  height: 100%;
  /* border-radius: inherit; */
}

.i {
  height: 75%;
  border-radius: 0.5rem; 
}

.s {
  height: 20%;
  justify-content: space-evenly;
  align-items: center;
  /* border-color: red; */
  padding-inline: 3%;

  .thn {
    width: 18%;
    height: 80%;

    img {
      border-radius: 0.625rem;
      /* border: 2px solid var(--orange); */
    }
  }
}
</style>
