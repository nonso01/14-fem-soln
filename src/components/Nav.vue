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
    <div class="l flex center">
      <div class="logo flex center bd">
        <img src="/logo.svg" alt="logo icon" />
      </div>
      <div class="links flex bd">
        <span class="nav-items transition" v-for="item in list">
          {{ item }}</span
        >
      </div>
    </div>
    <div class="i flex center">
      <div class="cart flex center" @click="handleShowCart">
        <span class="q" v-if="quantity > 0"> {{ quantity }}</span>
        <ShoppingCart stroke="var(--grayish-blue)" stroke-width="2.5" />
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

.cart {
  position: relative;

  .q {
    /* border-color: red; */
    padding-inline: 15%;
    background-color: var(--orange);
    position: absolute;
    top: -60%;
    left: 60%;
    max-width: 25px;
    color: var(--very-dark-blue);
    font-weight: bold;
    font-size: 0.9rem;
    border-radius: 5px;
  }

  svg:hover {
    stroke: var(--very-dark-blue);
  }
}
/* @media screen and (max-width: 500px) {} */
</style>
