<script setup>
import FallLimited from "./components/FallLimited.vue";
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
function handleAddToCart() {}
</script>

<template>
  <!-- <h1>E commerce site</h1> -->
  <FallLimited
    :handle-plus="handlePlus"
    :quantity="quantity"
    :handle-minus="handleMinus"
  />
</template>

<style scoped></style>
