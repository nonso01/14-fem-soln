<script setup>
import FallLimited from "./components/FallLimited.vue";
import Added from "./components/Added.vue";
import Cart from "./components/Cart.vue";
import { ref } from "vue";

const quantity = ref(0);
const maxQuantity = 20;

function handlePlus() {
  quantity.value += 1;
  quantity.value >= maxQuantity ? (quantity.value = maxQuantity) : void 0;
}
function handleMinus() {
  quantity.value -= 1;
  quantity.value <= 0 ? (quantity.value = 0) : void 0;
}
function handleAddToCart() {
  alert("added to cart");
}
</script>

<template>
  <!-- <FallLimited
    :handle-plus="handlePlus"
    :quantity="quantity"
    :handle-minus="handleMinus"
    :handle-add-to-cart="handleAddToCart"
  /> -->

  <!-- <Added /> -->
  <Cart :added="true" />
</template>

<style scoped></style>
