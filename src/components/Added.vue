<script setup>
import { CircleCheckBig } from "lucide-vue-next";
</script>

<template>
  <div class="flex a">
    <CircleCheckBig stroke-width="2" stroke="var(--very-dark-blue)" />
    <span><slot></slot></span>
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
  background-color: var(--orange);
}

span {
  color: var(--very-dark-blue);
  font-weight: bold;
  font-size: 0.7rem;
}

.lucide {
  animation: offset 0.35s ease 1;
}

@keyframes offset {
  from {
    scale: 0;
  }
  to {
    scale: 1;
  }
}
</style>
