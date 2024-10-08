<script setup>
import { ShoppingCart } from "lucide-vue-next";

const props = defineProps({
  handleShowCart: Function,
  quantity: Number,
});
const list = ["Collections", "Men", "Women", "About", "Contact"];
</script>

<template>
  <!-- media queries -->
  <div class="nav flex bd">
    <div class="l flex center bd">
      <div class="logo flex center bd">
        <img src="/logo.svg" alt="logo icon" />
      </div>
      <div class="links flex bd">
        <span class="nav-items transition" v-for="item in list">
          {{ item }}</span
        >
      </div>
    </div>
    <div class="i flex center bd">
      <div class="bd cart flex center" @click="handleShowCart">
        <ShoppingCart stroke="var(--very-dark-blue)" stroke-width="2.5" />
      </div>
      <div class="pfp flex center transition" @click="handleShowCart">
        <img src="/image-avatar.png" alt="user profile" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.nav {
  position: relative;
  width: 100dvw;
  height: 130px;
  justify-content: space-evenly;

  .l {
    width: 50%;
    justify-content: space-between;

    .links {
      width: 80%;
      justify-content: space-evenly;

      .nav-items {
        color: var(--dark-grayish-blue);
        font-weight: bold;
        &:hover {
          color: var(--very-dark-blue);
        }
      }
    }
  }

  .i {
    width: 20%;
    justify-content: space-evenly;

    .pfp {
      outline: 3px solid transparent;
      outline-offset: 4px;
      width: 3.125rem;
      aspect-ratio: 1;
      border-radius: 50%;

      &:hover {
        outline-color: var(--orange);
      }

      img {
        width: 100%;
        height: 100%;
      }
    }
  }
}
/* @media screen and (max-width: 500px) {} */
</style>
