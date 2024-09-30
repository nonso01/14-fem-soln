<script setup>
import { CircleCheckBig } from "lucide-vue-next";
</script>

<template>
  <div class="flex">
    <CircleCheckBig stroke-width="2" stroke="#ff7d1a" />
    <span>Added</span>
  </div>
</template>
<style scoped>
div {
  width: 7rem;
  height: 2rem;
  margin: 4%;
  justify-content: space-around;
  align-items: center;
  border-radius: 5px;
  border: 2px solid transparent;
  outline-offset: 2px;
  outline: 4px solid var(--pale-orange);
 /* animation: name duration timing-function delay iteration-count direction fill-mode; */
}

span {
  color: var(--orange);
  font-weight: bold;
}
</style>
