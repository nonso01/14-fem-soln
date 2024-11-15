<template>
  <div class="o"></div>
</template>

<style scoped>
html:has(div.o) {
  overflow-y: hidden;
  scrollbar-gutter: stable;
}
.o {
  position: absolute;
  z-index: 5;
  width: 100dvw;
  height: 100dvh;
  backdrop-filter: blur(0.3rem);
  background-color: rgb(29 32 37 / 0.2);
}
</style>
