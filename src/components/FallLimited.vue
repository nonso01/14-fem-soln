<script setup>
import { Plus, Minus, ShoppingCart } from "lucide-vue-next";
// import { ref } from "vue";

const props = defineProps({
  handlePlus: Function,
  handleMinus: Function,
  handleAddToCart: Function,
  quantity: Number,
});

const strokeColor = "#ff7d1a";
</script>

<template>
  <div class="f-l flex column bd">
    <div class="f-l-h flex column">
      <h4>Sneaker Company</h4>
      <h1>Fall Limited Edition Sneakers</h1>
    </div>

    <div class="f-l-p flex column">
      <p>
        These low-profile sneakers are your perfect casual wear companion.
        Featuring a durable rubber outer sole, they'll withstand everything the
        weather can offer.
      </p>
      <div class="prices flex">
        <p class="flex">
          <span class="bold">$125.00</span>
          <span class="discount flex center"> 50%</span>
        </p>
        <p class="strike">$250.00</p>
      </div>
    </div>

    <div class="f-l-b flex b">
      <div class="quantity flex">
        <Plus :stroke="strokeColor" stroke-width="3" @click="handlePlus" />
        <span> {{ quantity }}</span>
        <Minus :stroke="strokeColor" stroke-width="3" @click="handleMinus" />
      </div>
      <div class="add flex" @click="handleAddToCart">
        <ShoppingCart stroke-width="2.5" />
        <span>Add to cart</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* replace column class */
.f-l {
  width: 31.25rem;
  /* 26%; */
  height: 33.75rem;
  /* 60dvh; */

  justify-content: space-evenly;

  h1 {
    color: var(--very-dark-blue);
    text-wrap: pretty;
    font-size: 2.8rem;
  }

  h4,
  p {
    color: var(--dark-grayish-blue);
    line-height: 1.5;
    text-wrap: pretty;
  }

  .strike {
    text-decoration: line-through;
    font-weight: bold;
  }

  .bold {
    color: var(--very-dark-blue);
    font-size: x-large;
    font-weight: bold;
  }

  .discount {
    background-color: var(--very-dark-blue);
    color: var(--white);
    font-weight: bold;
    width: 2.81rem;
    height: 1.875rem;
    border-radius: 5px;
  }
  .f-l-h {
    flex-grow: 0.05;
    justify-content: space-between;
  }

  .f-l-p {
    flex-grow: 0.2;
    justify-content: space-between;

    .prices {
      flex-grow: 0.6;

      flex-direction: column;
      justify-content: space-around;

      p:not(.strike) {
        width: 30%;
        justify-content: space-between;
      }
    }
  }

  .f-l-b {
    flex-grow: 0.15;
    justify-content: space-between;

    span {
      font-weight: bold;
    }

    .quantity {
      flex-grow: 0.3;
      justify-content: space-between;
      align-items: center;
      background-color: var(--light-grayish-blue);
      border-radius: 0.5rem;
      svg {
        cursor: pointer;
        margin-inline: 5%;
      }
      span {
        color: var(--very-dark-blue);
      }
    }

    .add {
      flex-grow: 0.5;
      justify-content: center;
      align-items: center;
      background-color: var(--orange);
      border-radius: 0.5rem;
      cursor: pointer;
      svg,
      span {
        margin-inline: 5px;
        color: var(--very-dark-blue);
      }
    }
  }
}

@media screen and (max-width: 500px) {
  .f-l {
    width: 100%;
    border-color: red;
  }
}
</style>
