<script setup>
import { Trash2 } from "lucide-vue-next";
const props = defineProps({
  handleCheckout: Function,
  handleDeleteCart: Function,
  quantity: Number,
  total: Number,
  added: Boolean,
});
</script>

<template>
  <div class="cart flex column bd">
    <span class="title">Cart</span>
    <div class="d flex column">
      <span class="e" v-if="!added">Your cart is empty</span>
      <template v-if="added">
        <div class="d-p flex center">
          <div class="image"></div>
          <div class="calc">
            <p>Fall Limited Edition Sneaker</p>
            <p>
              $125.00 x {{ quantity }} <span class="bold"> ${{ total }}</span>
            </p>
          </div>
          <div><Trash2 stroke="#68707d" @click="handleDeleteCart" /></div>
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
  margin-inline: 5%;
}

p {
  color: var(--dark-grayish-blue);
  margin-block: 1.5%;
}
.lucide-trash2-icon:hover {
  stroke: red;
}
.bold {
  font-weight: bold;
  color: var(--very-dark-blue);
}

.cart {
  width: 22.5rem;
  aspect-ratio: 1.5/1;
  backdrop-filter: blur(0.625rem);
  box-shadow: 0 1rem 1rem rgb(0 0 0 / 0.15);
  border-radius: 0.625rem;
  justify-content: space-around;
}
.d {
  flex-grow: 0.65;
  min-height: 168.5px;
  justify-content: space-around;
  padding-inline: 4%;
  border-top: 2px solid var(--grayish-blue);

  span.e {
    font-weight: bold;
    color: var(--dark-grayish-blue);
    align-self: center;
  }
  .d-p {
    height: 39%;
    justify-content: space-between;
  }
  .d-c {
    height: 38%;
    background-color: var(--orange);
    border-radius: 0.7rem;
    font-weight: bold;
    color: var(--very-dark-blue);
    font-size: 1.1rem;
  }

  .image {
    width: 50px;
    aspect-ratio: 1 / 1;
    background-image: url("/image-product-1-thumbnail.jpg");
    background-size: cover;
    border-radius: 0.3rem;
  }

  .calc {
    width: 70%;
  }
}
</style>
