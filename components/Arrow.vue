<template>
  <font-awesome-icon
    :style="{ color: 'inherit' }"
    :icon="['fas', 'arrow-right']"
  />
</template>

<style scoped>
.Arrow {
  animation: 1s appear;
  margin: auto;
}

@keyframes appear {
  0% {
    opacity: 0;
  }
}
</style>
