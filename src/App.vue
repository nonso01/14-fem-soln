<script setup>
import FallLimited from "./components/FallLimited.vue";
import Added from "./components/Added.vue";
import Cart from "./components/Cart.vue";
import Nav from "./components/Nav.vue";
import Slider from "./components/Slider.vue";
import Overlay from "./components/Overlay.vue";
import { computed, ref } from "vue";

const maxQuantity = 20;
const price = 125;
const onesec = 1e3;
const quantity = ref(0);
const quantity_changed = ref(0);
const total = computed(() => quantity_changed.value * price);
const itemAdded = ref(false);
const itemAddedCopy = ref(false);
const itemDeleted = ref(false);
const showCart = ref(false);
const overlay = ref(false);

function handlePlus() {
  quantity.value += 1;
  quantity.value >= maxQuantity ? (quantity.value = maxQuantity) : void 0;
}
function handleMinus() {
  quantity.value -= 1;
  quantity.value <= 0 ? (quantity.value = 0) : void 0;
}
function handleAddToCart() {
  if (quantity.value > 0) {
    quantity_changed.value = quantity.value;
    itemAdded.value = true;
    itemAddedCopy.value = true;

    setTimeout(() => {
      itemAddedCopy.value = false;
    }, onesec);
  } else {
    itemAdded.value = false;
  }
}

function handleDeleteCart() {
  itemAdded.value = false;
  quantity_changed.value = 0;

  itemDeleted.value = true;
  setTimeout(() => {
    itemDeleted.value = false;
  }, onesec);
}

function handleOverlay() {
  overlay.value = !overlay.value;
}

function handleShowCart() {
  showCart.value = !showCart.value;
}
</script>

<template>
  <Transition name="fade">
    <Added v-if="itemAddedCopy"> items added </Added>
  </Transition>

  <Transition name="fade">
    <Added v-if="itemDeleted"> items deleted </Added>
  </Transition>

  <Nav :handle-show-cart="handleShowCart" :quantity="quantity_changed" />

  <Transition name="fade">
    <Cart
      v-if="showCart"
      :added="itemAdded"
      :quantity="quantity_changed"
      :total="total"
      :handle-delete-cart="handleDeleteCart"
    />
  </Transition>

  <div class="main flex">
    <Slider @click="handleOverlay" />

    <FallLimited
      :handle-plus="handlePlus"
      :quantity="quantity"
      :handle-minus="handleMinus"
      :handle-add-to-cart="handleAddToCart"
    />
  </div>

  <Transition>
    <Overlay @click="handleOverlay" v-if="overlay" />
  </Transition>

  <Transition>
    <Slider
      v-if="overlay"
      :overlay="overlay"
      :handle-overlay="handleOverlay"
      class="overlay"
    />
  </Transition>
</template>

<style>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.3s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition-property: opacity transform;
  transition-duration: 0.2s;
  transition-timing-function: ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translate(-10%);
}

#app {
  display: flex;
  flex-direction: column;
}

.main {
  margin-top: 3%;
  width: 80%;
  justify-content: space-between;
  align-items: center;
}

@media screen and (max-width: 1280px) {
  #app {
    .main {
      /* background-color: red; */
      border: 2px solid red;
      width: 80%;
    }
  }
}

@media screen and (min-width: 1980px) {
  #app {
    .main {
      width: max(60%, 1145px);
    }
  }
}

@media screen and (max-width: 600px) {
  #app {
    width: 100dvw;

    .main {
      width: 100%;
      flex: 1;
      margin: 0;
    }
  }
}
</style>
