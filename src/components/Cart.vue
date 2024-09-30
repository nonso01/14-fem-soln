<script setup>
const props = defineProps({
  handleCheckout: Function,
  added: Boolean,
});
</script>

<template>
  <div class="cart flex column bd">
    <span class="title bd">Cart</span>
    <div class="d flex column bd">
      <template v-if="added">
        <div class="d-p bd">
          <div class="image"></div>
          <div class="calc"></div>
        </div>
        <div class="d-c flex center">Checkout</div>
      </template>
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
  aspect-ratio: 1.5/1;
  background-color: var(--white);
  box-shadow: 0 1rem 1rem rgb(0 0 0 / 0.15);
  border-radius: 0.625rem;
  justify-content: space-around;
}
.d {
  /* border-top: 1.5px solid var(--grayish-blue); */
  flex-grow: 0.65;
  justify-content: space-around;
  padding-inline: 4%;
  .d-p {
    flex-grow: 0.5;
  }
  .d-c {
    flex-grow: 0.3;
    background-color: var(--orange);
    border-radius: 0.5rem;
    font-weight: bold;
    color: var(--very-dark-blue);
  }
}
</style>
