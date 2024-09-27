<script setup>
import { Plus, Minus } from "lucide-vue-next";
// import { ref } from "vue";

const maxQuantity = 20;
</script>

<template>
  <div class="f-l flex bd">
    <div class="f-l-h flex">
      <h4>Sneaker Company</h4>
      <h1>Fall Limited Edition Sneakers</h1>
    </div>

    <div class="f-l-p flex">
      <p>
        These low-profile sneakers are your perfect casual wear companion.
        Featuring a durable rubber outer sole, they'll withstand everything the
        weather can offer.
      </p>
      <div class="prices flex">
        <p class="flex">
          <span class="bold">$125.00</span>
          <span class="discount"> 50%</span>
        </p>
        <p class="strike">$250.00</p>
      </div>
    </div>

    <div class="f-l-b">
      <div class="quantity">
        <Plus stroke="#ff7d1a" />
        <span> {{ maxQuantity }}</span>
        <Minus stroke="#ff7d1a" />
      </div>
      <div class="add">
        <span>Add to cart</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* replace column class */
.f-l {
  width: 26%;
  height: 60dvh;

  flex-direction: column;
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
    padding-inline: 5%;
    padding-block: 2.8%;
    border-radius: 5px;
  }
  .f-l-h {
    flex-grow: 0.1;

    flex-direction: column;
    justify-content: space-between;
  }
  .f-l-p {
    /* height: 30%; */
    flex-grow: 0.2;

    flex-direction: column;
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
}
</style>
