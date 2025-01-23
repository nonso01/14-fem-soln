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
  <div class="f-l flex column">
    <div class="f-l-h flex column">
      <h3>SNEAKER COMPANY</h3>
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

    <div class="f-l-b flex">
      <div class="quantity flex">
        <Plus :stroke="strokeColor" stroke-width="3" @click="handlePlus" />
        <span> {{ quantity }}</span>
        <Minus :stroke="strokeColor" stroke-width="3" @click="handleMinus" />
      </div>
      <div class="add flex btn transition" @click="handleAddToCart">
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

  h3,
  p {
    color: var(--dark-grayish-blue);
    line-height: 1.5;
    text-wrap: pretty;
  }

  h3 {
    letter-spacing: 2px;
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
      border-radius: 0.6rem;
      svg {
        cursor: pointer;
        margin-inline: 5%;
      }
      span {
        color: var(--very-dark-blue);
        font-weight: bold;
        /* font-size: 1.15rem; */
      }
    }

    .add {
      flex-grow: 0.5;
      justify-content: center;
      align-items: center;
      background-color: var(--orange);
      border-radius: 0.6rem;
      cursor: pointer;
      svg,
      span {
        margin-inline: 1ch;
        color: var(--very-dark-blue);
        font-weight: bold;
        /* font-size: 1.15rem; */
      }
    }
  }
}

/* @media screen and (max-width: 1280px) {
#app {
 
}
} */

@media screen and (max-width: 600px) {
  #app {
    .f-l {
      width: 100%;
      padding-inline: 4%;
      justify-content: space-around;
    }

    .f-l-h {
      h1 {
        font-size: 2rem;
      }
      h3 {
        font-size: 0.85rem;
      }
    }

    .f-l-p {
      .prices {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;

        p.flex {
          width: 50%;
          align-items: center;
        }

        .strike {
          font-size: 1.2rem;
        }
        .bold {
          font-size: 2rem;
        }
      }
    }

    .f-l-b {
      height: 25%;
      flex-direction: column;

      div {
        flex-grow: 0.36;
        &.add {
          box-shadow: 0 0.725rem 2rem #ff7d1a60;
        }
      }
    }
  }
}
</style>
