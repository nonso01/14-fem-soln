<script setup>
import FallLimited from "./components/FallLimited.vue";
import Added from "./components/Added.vue";
import Cart from "./components/Cart.vue";
import { computed, ref } from "vue";

const maxQuantity = 20;
const price = 125;
const quantity = ref(0);
const total = computed(() => quantity.value * price);

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

function handleDeleteCart() {}
</script>

<template>
  <FallLimited
    :handle-plus="handlePlus"
    :quantity="quantity"
    :handle-minus="handleMinus"
    :handle-add-to-cart="handleAddToCart"
  />

  <!-- <Added /> -->
  <Cart :added="true" :quantity="quantity" :total="total" />
</template>

<style scoped></style>
