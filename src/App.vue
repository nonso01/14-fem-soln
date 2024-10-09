<script setup>
import FallLimited from "./components/FallLimited.vue";
import Added from "./components/Added.vue";
import Cart from "./components/Cart.vue";
import Nav from "./components/Nav.vue";
import Slider from "./components/Slider.vue";
import { computed, ref } from "vue";

const maxQuantity = 20;
const price = 125;
const quantity = ref(0);
const quantity_changed = ref(0);
const total = computed(() => quantity_changed.value * price);
const itemAdded = ref(false);
const showCart = ref(false);

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
  } else {
    itemAdded.value = false;
  }
}

function handleDeleteCart() {
  itemAdded.value = false;
  quantity_changed.value = 0;
}

// function handleCheckout() {
//   // for the cart ui
// }

function handleShowCart() {
  showCart.value = !showCart.value;
}
</script>

<template>
  <!-- <Nav :handle-show-cart="handleShowCart" :quantity="quantity_changed" /> -->

  <!-- <FallLimited
    :handle-plus="handlePlus"
    :quantity="quantity"
    :handle-minus="handleMinus"
    :handle-add-to-cart="handleAddToCart"
  /> -->

  <!-- <Added /> -->

  <!-- <Cart
    v-if="showCart"
    :added="itemAdded"
    :quantity="quantity_changed"
    :total="total"
    :handle-delete-cart="handleDeleteCart"
  /> -->

  <Slider />
</template>

<style scoped></style>
