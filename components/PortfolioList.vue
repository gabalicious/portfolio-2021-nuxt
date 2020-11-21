<template>
  <div class="portfolio-list">
    <PortfolioButton
      v-for="(opt, i) in options"
      :key="i"
      :class="isActive(i)"
      href="#"
    >
      {{ opt.name }}
    </PortfolioButton>
  </div>
</template>
<script>
export default {
  props: {
    options: {
      type: Array,
      default() {
        return []
      },
    },
  },
  data() {
    return {}
  },
  methods: {
    isActive(i = 0) {
      return i === 0 ? 'active' : 'not-active'
    },
  },
}
</script>

<style lang="scss">
.portfolio-list {
  position: relative;
  display: flex;

  flex-wrap: wrap;
  z-index: 2;
  width: 100%;
  min-height: 200px;
}
</style>
