<template>
  <transition name="details">
    <PortfolioDetailsModal
      v-if="query.category"
      :query="query"
    ></PortfolioDetailsModal>
  </transition>
</template>

<script>
export default {
  transition: {
    name: 'details',
  },
  data() {
    return {
      query: {},
    }
  },
  mounted() {
    /* eslint-disable */
    this.query = this.$route.query
  },
}
</script>
<style scoped lang="scss">
// only for desktop for now,
@media screen and (min-width: 1008px) {
  /* during entering and leaving : */
  .details-enter-active,
  .details-leave-active {
    position: absolute;

    transition: all 0.5 ease;
  }

  /* entering start */
  .details-enter {
    left: -200%;
  }

  /* entering end */
  .details-enter-to {
    left: 0;
  }

  /* leaving start */
  .details-leave {
    left: 0;
  }

  /* leaving end */
  .details-leave-to {
    left: 200%;
  }
}
</style>
