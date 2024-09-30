<script setup>
const props = defineProps({
  handleCheckout: Function,
});
</script>

<template>
  <div class="cart flex column">
    <span class="title">Cart</span>
    <div class="d">
      <div class="d-price">A</div>
      <div class="checkout"></div>
    </div>
  </div>
</template>

<style scoped>
.title {
  font-weight: bold;
  font-size: 1.1rem;
}

.cart {
  width: 360px;
  aspect-ratio: 1.3/1;
  background-color: var(--white);
  box-shadow: 0 1rem 1rem rgb(0 0 0 / 0.15);
  border-radius: 0.625rem;
  justify-content: space-around;
}
.d {
  /* border-top: 1px solid red; */
  height: 50%;
  background-color: red;
}
</style>
