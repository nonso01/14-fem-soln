<script setup>
import FallLimited from "./components/FallLimited.vue";
import Added from "./components/Added.vue";
import Cart from "./components/Cart.vue";
import { computed, ref } from "vue";

const maxQuantity = 20;
const price = 125;
const quantity = ref(0);
const total = computed(() => quantity.value * price);
const itemAdded = ref(false);

function handlePlus() {
  quantity.value += 1;
  quantity.value >= maxQuantity ? (quantity.value = maxQuantity) : void 0;
}
function handleMinus() {
  quantity.value -= 1;
  quantity.value <= 0 ? (quantity.value = 0) : void 0;
}
function handleAddToCart() {
  // work on here
  quantity.value > 0 ? (itemAdded.value = true) : void 0;
  console.log(itemAdded.value);
}

function handleDeleteCart() {
  alert("delete cart");
}
</script>

<template>
  <FallLimited
    :handle-plus="handlePlus"
    :quantity="quantity"
    :handle-minus="handleMinus"
    :handle-add-to-cart="handleAddToCart"
  />

  <!-- <Added /> -->
  <Cart
    :added="itemAdded"
    :quantity="quantity"
    :total="total"
    :handle-delete-cart="handleDeleteCart"
  />
</template>

<style scoped></style>
