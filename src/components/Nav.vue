<script setup>
import { ShoppingCart, Menu, X } from "lucide-vue-next";
import { ref } from "vue";
import Cart from "./Cart.vue";

const props = defineProps({
  handleShowCart: Function,
  handleShowMenu: Function,
  quantity: Number,
  showMenu: Boolean,
});

const scrollLeft = ref(0);
const scrollWidth = ref(0);

const list = ["Collections", "Men", "Women", "About", "Contact"];

function handleScrollNav({ target }) {
  const { offsetWidth, offsetLeft } = target;
  scrollWidth.value = `${offsetWidth}px`;
  scrollLeft.value = `${offsetLeft}px`;
}
</script>

<template>
  <!-- media queries -->
  <div class="nav flex">
    <div class="l flex center">
      <div class="logo flex center">
        <Menu class="logo-menu hide" stroke-width="3" @click="handleShowMenu" />
        <img src="/logo.svg" alt="logo icon" />
      </div>
      <div class="links flex" :class="{ m: showMenu }">
        <X class="hide link-cancel" stroke-width="3" @click="handleShowMenu" />
        <span
          class="nav-items transition pointer"
          v-for="item in list"
          @click="handleScrollNav"
        >
          {{ item }}</span
        >
      </div>
    </div>
    <div class="i flex center">
      <div class="cart flex center pointer" @click="handleShowCart">
        <span class="q" v-if="quantity > 0"> {{ quantity }}</span>
        <ShoppingCart stroke="var(--grayish-blue)" stroke-width="2.5" />
      </div>
      <div class="pfp flex center transition pointer" @click="handleShowCart">
        <img src="/image-avatar.png" alt="user profile" />
      </div>
    </div>

    <div
      class="scroll-line transition"
      :style="{ left: scrollLeft, width: scrollWidth }"
    ></div>
  </div>
</template>

<style scoped>
.nav {
  position: relative;
  width: 75dvw;
  height: 120px;
  justify-content: space-between;
  border-bottom: 1px solid var(--grayish-blue);

  .l {
    width: 60%;
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

.scroll-line {
  background-color: var(--orange);
  position: absolute;
  bottom: 0;
  border-radius: 0.5rem;
  height: 0.5rem;
}
@media screen and (min-width: 1980px) {
  #app {
    .nav {
      width: min(75dvw, 1440px);
    }
  }
}

@media screen and (max-width: 600px) {
  #app {

    .scroll-line {
      display: none;
    }

    .nav {
      width: 100%;
      height: 80px;
      /* border: none; */
    }

    .links {
      /* display: none; */
      background-color: white;
      position: absolute;
      z-index: 20;
      width: 65dvw;
      height: 100dvh;
      top: 0;
      left: -80%;
      transition-duration: 200ms;
      padding: 5%;
      flex-direction: column;
      justify-content: normal;

      .nav-items {
        margin-block: 5%;
        color: var(--very-dark-blue);
      }
      .link-cancel {
        margin-bottom: 15%;
      }
    }

    .m {
      left: 0;
    }

    .logo-menu,
    .link-cancel {
      display: block;
    }

    .l {
      width: 52%;
      .logo {
        width: 100%;
        justify-content: space-evenly;
      }
    }

    .i {
      width: 30%;
      .pfp {
        width: 2.2rem;
      }
    }
  }
}
</style>
