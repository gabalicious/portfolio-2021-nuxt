<template>
  <transition name="home">
    <div class="container">
      <PortfolioSelector></PortfolioSelector>
    </div>
  </transition>
</template>

<script>
export default {
  transition: {
    name: 'home',
  },
}
</script>

<style scoped lang="scss">
// only for desktop for now,
@media screen and (min-width: 1008px) {
  /* during entering and leaving : */
  .home-enter-active,
  .home-leave-active {
    position: absolute;
    transition: all 0.4s ease;
  }

  /* entering start */
  .home-enter {
    left: -200%;
  }

  /* entering end */
  .home-enter-to {
    left: 0;
  }

  /* leaving start */
  .home-leave {
    left: 0;
  }

  /* leaving end */
  .home-leave-to {
    left: 200%;
  }
}
.container {
  margin: 0 auto;
  min-height: 100vh;
  min-width: 100vw;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
</style>
