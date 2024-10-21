<script setup>
import { CircleCheckBig } from "lucide-vue-next";
</script>

<template>
  <div class="flex a">
    <CircleCheckBig stroke-width="2" stroke="#ff7d1a" />
    <span>items added</span>
  </div>
</template>
<style scoped>
div {
  position: absolute;
  top: 10%;
  z-index: 2;
  width: 7.5rem;
  height: 2rem;
  justify-content: space-around;
  align-items: center;
  border-radius: 5px;
  border: 2px solid transparent;
  outline-offset: 2px;
  outline: 4px solid var(--pale-orange);
  background-color: var(--white);
  /* animation: name duration timing-function delay iteration-count direction fill-mode; */
}

span {
  color: var(--orange);
  font-weight: bold;
  font-size: .8rem;
}
</style>
