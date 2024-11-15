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
  width: 100dvw;
  height: 100dvh;
  
  background-color: rgb(29 32 37 / 0.2);
}
</style>
